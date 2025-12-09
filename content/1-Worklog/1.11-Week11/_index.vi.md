---
title: "Worklog Tuần 11"
date: "2025-11-23"
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu tuần 11:

- Triển khai đầy đủ các dịch vụ đã đề ra trong dự án

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc                       | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | ------------------------------- | ------------ | --------------- | -------------- |
| 2   | - Thực hiện project và test lỗi | 17/11/2025   | 17/11/2025      |                |
| 3   | - Thực hiện project và test lỗi | 18/11/2025   | 18/11/2025      |                |
| 4   | - Thực hiện project và test lỗi | 19/11/2025   | 19/11/2025      |                |
| 5   | - Thực hiện project và test lỗi | 20/11/2025   | 20/11/2025      |                |
| 6   | - Thực hiện project và test lỗi | 21/11/2025   | 21/11/2025      |                |

### Kết quả đạt được tuần 11:

- Viết code về dự án và test lỗi
- Xây dựng, triển khai và quản lý ứng dụng Serverless với viết mẫu IaC bằng AWS SAM/CloudFormation, API Gateway, DynamoDB, Cognito , invite/redeem, SSO Google
- Thiết lập monitoring và alerting toàn diện với CloudWatch:
  - Tạo monitoring-alarms.yaml cho cả Identity và Academic services
  - Cảnh báo Lambda: Lỗi > 5%, Thời gian thực thi > p99, Throttles, Số lượng thực thi đồng thời
  - Cảnh báo API Gateway: Lỗi client 4XX, Lỗi server 5XX, Độ trễ
  - Cảnh báo DynamoDB: Throttles đọc/ghi, Dung lượng tiêu thụ
  - Chủ đề SNS: tcm-pipeline-notifications để gửi cảnh báo
  - Đăng ký email để nhận thông báo real-time
  - Bảng điều khiển CloudWatch để trực quan hóa metrics (có thể thêm sau)
  - Chính sách lưu trữ 30 ngày để tối ưu chi phí
