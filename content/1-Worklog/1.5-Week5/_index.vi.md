---
title: "Worklog Tuần 5"
date: "2025-10-12"
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần 5:

- Khám phá và hiểu tổng quan về AI/ML trên AWS.
- Tìm hiểu các dịch vụ AWS ML cơ bản: SageMaker, Rekognition, Comprehend, Kendra, Translate, Polly.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                               |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | -------------------------------------------- |
| 2   | - Tìm hiểu tổng quan về AI/ML trên AWS <br> - Tìm hiểu các dịch vụ hỗ trợ ML: SageMaker, Rekognition, Comprehend, Kendra, Translate, Polly                                                                                                                                                                                                                                                                                                                                                                                                                        | 06/10/2025   | 06/10/2025      | <https://cloudjourney.awsstudygroup.com/vi/> |
| 3   | - Tìm hiểu AWS và các loại dịch vụ <br>&emsp; + Cài đặt và khởi tạo Khởi tạo Amazon SageMaker Studio <br>&emsp; + Lấy code + dữ liệu thử nghiệm <br>&emsp; + Chuẩn bị dữ liệu: upload bộ dữ liệu lên Amazon S3 <br>&emsp; + sử dụng SageMaker Data Wrangler để phân tích, chuyển đổi, feature-engineering <br>&emsp; + Sử dụng Amazon SageMaker Feature Store để lưu trữ feature, quản lý metadata, xuất dữ liệu cho training <br>&emsp; + Train/Tune/Deploy XGBoost <br>&emsp; + Deploy model dưới dạng một HTTPS endpoint <br>&emsp; + Đánh giá hiệu suất model | 07/10/2025   | 07/10/2025      | <https://000200.awsstudygroup.com/>          |
| 4   | - Thực hành xác thực với Amazon Cognito <br>&emsp; + Chuẩn bị môi trường: tải mã nguồn mẫu, dùng AWS SAM để deploy back-end + front-end <br>&emsp; + Tạo User Pool trong Cognito <br> &emsp; + Tạo API + Lambda functions <br> &emsp; + Triển khai front-end web + gọi API để test flow user                                                                                                                                                                                                                                                                      | 08/10/2025   | 08/10/2025      | <https://000081.awsstudygroup.com/>          |
| 5   | - Thực hành Cloudfront VỚI S3 <br>&emsp; + Tạo Amazon S3 <br>&emsp; + Tải lên file INDEX.HTML <br>&emsp; + Cấu hình Amazon CloudFront                                                                                                                                                                                                                                                                                                                                                                                                                             | 09/10/2025   | 09/10/2025      | <https://000094.awsstudygroup.com/>          |
| 6   | - Thực hành triển khai một directory Managed AD trên <br> - Triển khai EC2 instance trong cùng VPC AWS <br> - Kiểm tra kết nối giữa các server/instance trong domain                                                                                                                                                                                                                                                                                                                                                                                              | 10/10/2025   | 10/10/2025      | <https://000095.awsstudygroup.com/>          |

### Kết quả đạt được tuần 5:

- Có thực hành thực tế với công cụ SageMaker Studio + Data Wrangler + Feature Store + S3
- Hiểu cách lưu trữ, xử lý dữ liệu, quản lý feature và dữ liệu training
- Biết cách deploy model làm endpoint production
- Hiểu rõ cách sử dụng Cognito để quản lý đăng ký, đăng nhập, xác thực người dùng mà không cần tự xây hệ thống auth từ đầu.
- Biết cách kết hợp Cognito + Lambda + API Gateway + front-end để xây ứng dụng web serverless có xác thực người dùng.
- Biết cách triển khai một Active Directory đầy đủ trên AWS — không cần tự cài Windows Server + domain controller thủ công.
