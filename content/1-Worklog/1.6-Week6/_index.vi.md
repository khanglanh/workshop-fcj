---
title: "Worklog Tuần 6"
date: "2025-10-19"
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6:

- Thực hành xây dựng ứng dụng Serverless-Document Management System Series
- Nâng cao kỹ năng xây dựng ứng dụng Serverless
- Thành thạo Hosting ứng dụng Web

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                                                                    |
| --- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | --------------------------------------------------------------------------------- |
| 2   | - Xây dựng một ứng dụng quản lý tài liệu <br> - sử dụng DMS + Lambda <br>&emsp; + Tạo bảng với DynamoDB <br>&emsp; +Tạo các Lambda function: liệt kê, tạo dữ liệu, xóa dữ liệu <br>&emsp; + Kiểm tra các function                                                                                                                                                                                                                                                                                                          | 13/10/2025   | 13/10/2025      | <https://000133.awsstudygroup.com/>                                               |
| 3   | - Triển Khai Front-end <br>&emsp; + Thiết Lập API Gateway bằng Lambda function <br>&emsp; + Kiểm Tra API Với Postman <br>&emsp; + Kiểm Tra API Với Front-end <br> <br> -Sử dụng Amplify Authentication và Storage <br>&emsp; + Cài đặt Amplify CLI <br>&emsp; + Clone project mẫu từ GitHub <br>&emsp; + Khởi tạo Amplify project bằng amplify init <br>&emsp; + Thiết lập Authentication cho ứng dụng <br>&emsp; + Thiết lập Storage <br>&emsp; + Triển khai frontend + backend + test <br>&emsp; + Cấu hình Access Level | 14/10/2025   | 14/10/2025      | <https://000135.awsstudygroup.com/> <br> <br> <https://000134.awsstudygroup.com/> |
| 4   | - **Thực hành triển khai ứng dụng với SAM:** <br>&emsp; + Cài đặt và khởi tạo dự án dùng AWS SAM <br>&emsp; + Tạo User Pool + Identity Pool của Amazon Cognito <br> &emsp; + Tạo bucket S3 <br>&emsp; + Deploy frontend + backend thông qua SAM & S3 <br>&emsp; + Cấu hình API endpoints + Lambda functions để xử lý API <br>&emsp; + Kiểm thử toàn bộ flow                                                                                                                                                                | 15/10/2025   | 15/10/2025      | <https://000136.awsstudygroup.com/>                                               |
| 5   | - Thiết lập trang web SSL S3 Static <br>&emsp; + Thiết lập lại ứng dụng web bằng AWS SAM <br>&emsp; + Tạo Miền Và Hosted Zone: <br>&emsp; + Chuẩn bị mã nguồn / project, build & deploy với AWS SAM / AWS CLI <br>&emsp; + Tạo và cấu hình domain & Hosted Zone với Amazon Route 53 <br>&emsp; + Tạo chứng chỉ SSL với AWS Certificate Manager <br>&emsp; + Tạo Amazon CloudFront Distributionstribution <br>&emsp; + <br>&emsp; + Triển khai website tĩnh → kiểm tra truy cập qua HTTPS + domain + CDN                    | 16/10/2025   | 16/10/2025      | <https://000137.awsstudygroup.com/>                                               |
| 6   | - Thực hành tích hợp Amazon OpenSearch với DynamoDB Stream                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | 17/10/2025   | 17/10/2025      | <https://000138.awsstudygroup.com/>                                               |

### Kết quả đạt được tuần 6:

- Hiểu AWS là gì và nắm được các nhóm dịch vụ cơ bản:
- Biết cách xây dựng một ứng dụng full stack serverless — front-end host trên S3, backend là Lambda + API Gateway, dữ liệu lưu trên DynamoDB.
- Biết cách sử dụng Amplify để xây dựng ứng dụng web/mobile serverless — không cần tự quản lý server.
- Sử dụng CloudWatch để giám sát hệ thống, thu thập metrics, logs, tạo alarm và dashboard cho EC2 và ứng dụng.
- Biết cách host website tĩnh trên S3 + cấu hình SSL/TLS
- Biết cách thiết lập domain riêng + DNS (Route 53) + liên kết domain với CloudFront & S3 + SSL certificate
- Hiểu cách tích hợp CDN (CloudFront)
