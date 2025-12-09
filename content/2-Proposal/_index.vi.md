---
title: "Bản đề xuất"
date: 2025-09-30
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Teaching Center Management System

## Giải pháp AWS Serverless cho dự án quản lý trung tâm dạy học

### 1. Tóm tắt điều hành

Dự án tập trung triển khai nền tảng LMS (Learning Management System) phục vụ nghiệp vụ đào tạo cốt lõi, tương đương phạm vi sử dụng của hệ thống tương tự như lms-hcmuni.fpt.edu.vn. Cụ thể, phạm vi bao gồm 2 phần: quản lý học vụ và xác thực/định danh và phân quyền.

Mục tiêu là cung cấp các khả năng LMS trọng yếu: quản lý môn học và lớp học; lịch học; tìm kiếm và ghi danh bằng mã enrollKey; dashboard theo vai trò (Admin, Teacher, Student); quản lý hồ sơ giảng viên/học viên; quản lý tài liệu môn học trên S3 (tạo thư mục, upload, tải xuống có kiểm tra ghi danh); và luồng import dữ liệu hàng loạt từ Excel để khởi tạo nhanh dữ liệu học thuật ban đầu. Phần xác thực/định danh và phân quyền bảo đảm đăng nhập/xác thực với Amazon Cognito (hỗ trợ OAuth/Google), lời mời tham gia (invite/redeem), cấp/đổi mật khẩu, làm mới token, hồ sơ người dùng, cùng cơ chế phân quyền theo vai trò để bảo vệ tài nguyên học vụ.

Trong tương lai, hệ thống có thể mở rộng dần sang các module khác (CRM, thanh toán, HRM…) và cân nhắc tích hợp AI/IoT khi cần, nhưng không thuộc phạm vi triển khai hiện tại.

### 2. Tuyên bố vấn đề

**Vấn đề hiện tại**

Ở bối cảnh LMS, nhiều đơn vị đào tạo đang vận hành rời rạc các bước: tạo môn học/lớp học, công bố lịch, ghi danh học viên, quản lý tài liệu, và truy cập hồ sơ — thường trải qua nhiều công cụ khác nhau. Điều này dẫn đến dữ liệu phân mảnh, khó kiểm soát quyền truy cập, quy trình ghi danh thủ công (dễ sai) và trải nghiệm người dùng không nhất quán giữa giảng viên và học viên.

Khi số lượng môn/lớp tăng, thiếu một cơ chế phân quyền thống nhất theo vai trò, xác thực tin cậy (SSO/OAuth), và các API học vụ rõ ràng để phục vụ dashboard theo vai trò. Việc thiếu kênh import dữ liệu hàng loạt cũng gây chậm trễ khi khởi tạo học kỳ mới.

**Giải pháp**

Nền tảng được triển khai trên kiến trúc AWS Serverless, tập trung giải quyết hai trụ cột:

- Phần xác thực/định danh và phân quyền: Amazon Cognito cho xác thực (email/password, Google OAuth), lời mời (invite/redeem), đặt lại/đổi mật khẩu, refresh token, hồ sơ người dùng; cấp quyền theo vai trò (ADMIN/TEACHER/STUDENT) để bảo vệ API và tài nguyên học vụ.
- Phần học vụ: API quản lý môn học/lớp học, tìm kiếm hợp nhất, ghi danh bằng enrollKey (kích hoạt PRE_ENROLLED → ACTIVE), dashboard theo vai trò, hồ sơ giảng viên/học viên, và quản lý tài liệu môn học trên S3 (tạo thư mục, presigned upload/download có kiểm tra ghi danh). Hỗ trợ import Excel để khởi tạo dữ liệu nhanh và rollback toàn phần khi lỗi.

Luồng truy cập: CloudFront → S3 (nội dung tĩnh) và API Gateway → Lambda → DynamoDB (dữ liệu học vụ/định danh) với CloudWatch/SNS/Secrets Manager cho giám sát và bảo mật. CI/CD được thực hiện qua GitLab Runner kết hợp AWS SAM CLI.

**Lợi ích và hoàn vốn đầu tư (ROI)**

- _Tăng tốc độ phát triển và triển khai_: CI/CD tự động với GitLab Runner và CloudFormation giúp giảm thời gian phát hành tính năng mới từ vài ngày xuống còn vài giờ.
- _Tối ưu chi phí vận hành_: Kiến trúc Serverless (Lambda, DynamoDB, API Gateway) chỉ tính phí khi có request, tiết kiệm 40–60% chi phí so với EC2 truyền thống.
- _Bảo mật toàn diện_: Secrets Manager và Cognito kết hợp IAM giúp bảo vệ dữ liệu nhạy cảm và kiểm soát truy cập chặt chẽ.
- _Hiệu suất truy cập cao_: CloudFront CDN giúp tăng tốc độ truy cập và giảm độ trễ 50–70%.
- _Khả năng mở rộng linh hoạt_: Hệ thống tự động mở rộng theo lưu lượng, không cần can thiệp thủ công.
- _Giám sát chủ động_: CloudWatch + SNS cung cấp cảnh báo real-time, giúp đội ngũ kỹ thuật xử lý sự cố kịp thời.

### 3. Kiến trúc giải pháp

![Teaching center management](/workshop-fcj/images/2-Proposal/project1_architecture_diagram_vi.jpg)

#### Mô tả chi tiết

1.  **User Request Flow**

    - Người dùng mở trình duyệt và truy cập ứng dụng thông qua tên miền.
    - **Amazon CloudFront** nhận request:
      - Kiểm tra cache để trả nội dung tĩnh (HTML/CSS/JS) từ **S3** nếu có.
      - Nếu nội dung chưa có trong cache, CloudFront fetch từ S3, trả lại cho user với độ trễ thấp.
    - User nhận được frontend và tương tác với giao diện, phát sinh các request API.

2.  **Authentication & API Handling**

    - Khi user đăng nhập:
      - **Amazon Cognito** xác thực thông tin đăng nhập (username/password hoặc OAuth).
      - Cognito tạo JWT token và trả về client.
    - Frontend gửi request API kèm token JWT tới **API Gateway**.
    - API Gateway thực hiện:
      - Kiểm tra JWT token với Cognito.
      - Nếu token hợp lệ, request được chuyển tới Lambda function tương ứng.
      - Nếu token không hợp lệ, API Gateway trả về lỗi 401 Unauthorized.

3.  **Lambda Processing & Data Access**

    - **AWS Lambda** thực thi logic nghiệp vụ:
      - Quản lý học viên, điểm danh, đăng ký khóa học, cập nhật kết quả, lịch học…
      - Khi cần truy cập thông tin nhạy cảm (API key, mật khẩu DB), Lambda gọi **AWS Secrets Manager**.
    - Lambda đọc/ghi dữ liệu vào **Amazon DynamoDB**:
      - DynamoDB lưu dữ liệu theo mô hình NoSQL, tối ưu read/write, tự động mở rộng khi lưu lượng tăng.
      - Hỗ trợ truy vấn theo khóa chính (PK) hoặc secondary index (GSI).
    - Lambda ghi log về **CloudWatch Logs**, bao gồm: request, error, execution metrics.

4.  **Security & Access Control**

    - **Amazon Cognito**: xác thực người dùng và quản lý phiên làm việc, hỗ trợ OAuth/Google Sign-In.
    - **IAM Roles & Policies**: kiểm soát quyền truy cập giữa các dịch vụ AWS (Lambda, DynamoDB, S3).
    - **API Gateway Authorization**: xác thực JWT token từ Cognito trước khi cho phép truy cập Lambda.
    - **Secrets Manager**: bảo vệ thông tin nhạy cảm (API keys, database credentials), cho phép Lambda truy cập an toàn.

5.  **Monitoring & Alerts**

    - **CloudWatch Logs** thu thập logs từ Lambda và API Gateway.
    - **Metrics & Alarms**:
      - Tạo metrics từ logs (CPU, error rate, latency, request count).
      - Cấu hình CloudWatch Alarms, khi vượt ngưỡng, kích hoạt alert.
    - **Amazon SNS** gửi cảnh báo real-time đến team vận hành qua email hoặc endpoint HTTP/SMS.
    - Kết hợp CloudTrail + CloudWatch để audit hành động API và bảo mật tổng thể.

6.  **CI/CD & Deployment**

    - **GitLab**: lưu trữ source code và quản lý version control.
    - **GitLab Runner**:
      - Tự động trigger khi có code push hoặc merge request.
      - Chạy CI/CD pipeline với các stage: test, build, deploy.
      - Cài đặt dependencies và chạy unit test.
      - Build artifact (ZIP package cho Lambda).
    - **AWS SAM CLI / CloudFormation**:
      - GitLab Runner sử dụng AWS SAM CLI để deploy.
      - Triển khai hoặc cập nhật toàn bộ hạ tầng AWS (API Gateway, Lambda, DynamoDB, S3, IAM Role).
      - Đảm bảo hạ tầng theo mô hình IaC, nhất quán giữa môi trường Dev/Prod.
    - CI/CD tự động, giảm lỗi, rút ngắn thời gian triển khai.

7.  **Summary**
    - **Request Path**: User → CloudFront → API Gateway → Lambda (via Cognito Auth) → DynamoDB → Lambda → API Gateway → CloudFront → User.
    - **Security Path**: Cognito Authentication → API Gateway Authorization → IAM Policies → Secrets Manager.
    - **Monitoring**: CloudWatch Logs & Metrics → Alarms → SNS.
    - **CI/CD Path**: GitLab → GitLab Runner → AWS SAM CLI → CloudFormation → AWS Resources.

#### Dịch vụ AWS sử dụng

|                     | Services                                                    | Description                                                         |
| ------------------- | ----------------------------------------------------------- | ------------------------------------------------------------------- |
| **Frontend & CDN**  | CloudFront, S3                                              | Phân phối nội dung, lưu trữ tĩnh                                    |
| **Backend & Logic** | API Gateway, Lambda, DynamoDB, Secrets Manager, Cognito     | Serverless logic, dữ liệu, xác thực                                 |
| **Monitoring**      | CloudWatch Logs, CloudWatch Alarms, CloudWatch Metrics, SNS | Giám sát, cảnh báo, thu thập metrics                                |
| **CI/CD & IaC**     | CloudFormation, SAM                                         | Triển khai tự động và quản lý cơ sở hạ tầng (kết hợp GitLab Runner) |

### 4. Triển khai kỹ thuật

_Các giai đoạn triển khai_

- Giai đoạn phát triển (Development)
  - Hoàn thiện các logic nghiệp vụ và main flow cho các hàm Lambda.
  - Viết file `template.yaml` mô tả tài nguyên: API Gateway, Lambda Functions, DynamoDB, Cognito.
  - Sử dụng AWS SAM CLI triển khai mã và `template.yaml` lên LocalStack để kiểm thử cục bộ.
- Giai đoạn deploy:
  - Dùng AWS SAM CLI để triển khai mã và `template.yaml` lên môi trường AWS thật.
  - Cấu hình GitLab CI/CD với GitLab Runner để tự động hóa quy trình build và deploy.

_Yêu cầu kỹ thuật_

- Có tài khoản AWS sử dụng Free Tier triển khai và sử dụng các tài nguyên bình thường.
- File `template.yaml` phải được cấu hình chính xác để mô tả đầy đủ các dịch vụ.
- Hệ thống cần có cơ chế rollback tự động khi xảy ra lỗi triển khai.

### 5. Lộ trình & Mốc triển khai

- _Trước thực tập (Tuần 0)_: Học các dịch vụ AWS để chuẩn bị cho project. Khảo sát, phân tích yêu cầu và các bộ phận liên quan của các trung tâm thật (Nhân sự, Đào tạo, Tuyển sinh).
- _Thực tập (Tuần 1-12):_
  - Tuần 1–3: Thiết kế hệ thống, giao diện, kiến trúc tổng thể và chuẩn bị tài liệu (proposal, diagram, template SAM).
  - Tuần 4–8: Phát triển các module cốt lõi (quản lý học viên, giảng viên, lớp học, xác thực người dùng). Kiểm thử cục bộ bằng LocalStack.
  - Tuần 9–11: Tích hợp các module, hoàn thiện CI/CD pipeline, triển khai hệ thống lên môi trường AWS thật.
  - Tuần 12: Kiểm thử tổng thể, đánh giá kết quả, hoàn thiện báo cáo và đề xuất hướng phát triển tiếp theo.
- _Sau thực tập (Định hướng mở rộng – Tuần 12 về sau): Nâng cấp hệ thống, tối ưu hiệu năng, và tích hợp công nghệ AI (phân tích học tập cá nhân hóa) cùng IoT (quản lý lớp học thông minh)._

### 6. Ước tính ngân sách

Có thể xem chi phí trên [AWS Pricing Calculator](https://calculator.aws/#/estimate?id=124ba62af284b2bb59152497a349995d8342c2a5)  
Hoặc tải tệp ước tính ngân sách [pdf](/files/project_1_estimate.pdf) | [csv](/files/project_1_estimate.csv) | [json](/files/project_1_estimate.json)

_Chi phí hạ tầng_

- S3 Standard: 0.32 USD/tháng (10 GB, 5.000 PUT requests, 100.000 GET requests).
- CloudFront: 1.33 USD/tháng (10 GB, Data transfer out to origin 0.1 GB, Number of requests (HTTPS) 100.000).
- Amazon API Gateway: 0.38 USD/tháng (300.000 request).
- AWS Lambda Function - Include Free Tier: 0.00 USD/tháng (400.000 request, 512 MB lưu trữ).
- Amazon DynamoDB: 0.62 USD/tháng (Data storage 2 GB, 50.000 Write/, 200.000 Read)
- Amazon Cognito Lite Tier: 0.00 USD/tháng (500 MAUs)
- Amazon CloudWatch: 2.10 USD/tháng (3 custom metric, Log 1GB, 1 dashboard, 2 alarms)
- AWS Secrets Manager: 0.40 USD/tháng (1 secret)
- Amazon SNS: 0.00 USD/tháng (1M request, 1M lambda deliveries)
- AWS CloudFormation: 0.00 USD/tháng
- GitLab Runner: 0.00 USD/tháng (self-hosted hoặc GitLab Free Tier)

  _Tổng_: 5.15 USD/tháng, 61.80 USD/12 tháng

### 7. Đánh giá rủi ro

_Ma trận rủi ro_

- Lỗi cấu hình AWS (IAM, Lambda, API Gateway, Cognito): Ảnh hưởng cao, xác suất trung bình
- Quá giới hạn Free Tier AWS: Ảnh hưởng trung bình, xác suất thấp.
- Mất dữ liệu trên S3/DynamoDB: Ảnh hưởng cao, xác suất thấp.
- Lỗi tích hợp giữa các dịch vụ AWS: Ảnh hưởng trung bình, xác suất thấp.
- Tấn công từ bên ngoài (SQL injection, XSS, unauthorized access): Ảnh hưởng cao, xác suất thấp đến trung bình

_Chiến lược giảm thiểu_

- Cấu hình AWS: Kiểm tra kỹ file `template.yaml`, thử triển khai trên LocalStack trước khi deploy thật.
- Vượt giới hạn Free Tier: Theo dõi chi phí thường xuyên, thiết lập cảnh báo chi tiêu (Billing Alert), tối ưu tài nguyên.
- Mất dữ liệu: Bật S3 Versioning, sao lưu định kỳ dữ liệu DynamoDB.
- Lỗi tích hợp dịch vụ: Đảm bảo các dịch vụ hoạt động cùng Region, kiểm tra IAM Role và quyền truy cập chéo giữa các service.
- Bảo mật ứng dụng: Validate input ở Lambda layer, sử dụng Cognito để xác thực chặt chẽ, cấu hình CORS đúng cách trên API Gateway, áp dụng principle of least privilege cho IAM roles, bật CloudWatch và API Gateway logging để audit

_Kế hoạch dự phòng_

- Khi gặp lỗi deploy: rollback bằng AWS SAM CLI hoặc khôi phục version Lambda trước đó qua CloudFormation stack.
- Khi vượt ngân sách: tạm dừng các dịch vụ không thiết yếu, tối ưu lại kiến trúc và tài nguyên sử dụng.
- Khi có sự cố bảo mật: rà soát log CloudWatch, vô hiệu hóa user/token bị compromised qua Cognito, review IAM permissions, cách ly Lambda function bị ảnh hưởng

### 8. Kết quả kỳ vọng

- Hệ thống quản lý trung tâm dạy học được triển khai thành công trên nền tảng AWS Serverless, đảm bảo hoạt động ổn định, bảo mật, dễ mở rộng.
- Tối ưu chi phí vận hành nhờ tận dụng AWS Free Tier và kiến trúc serverless, giảm chi phí đầu tư hạ tầng ban đầu.
- Đảm bảo hiệu suất truy cập cao, thời gian phản hồi nhanh và khả năng mở rộng linh hoạt.
- Đảm bảo an toàn dữ liệu với các cơ chế backup, versioning, và kiểm soát truy cập chặt chẽ.
- Tích hợp CI/CD giúp tự động hóa triển khai, kiểm thử và rollback, đảm bảo quy trình phát triển hiệu quả và đáng tin cậy.
