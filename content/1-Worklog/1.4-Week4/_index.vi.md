---
title: "Worklog Tuần 4"
date: "2025-10-05"
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4:

- Nắm vững kiến thức nền tảng + nâng cao về Networking trên AWS
- Thực hành triển khai các dịch vụ Compute & Container
- Nâng cao kỹ năng xây dựng ứng dụng Serverless

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                      |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------- |
| 2   | - **Triển khai Lightsail Database:** <br> &emsp; + Triển khai máy chủ Wordpress Instance <br> &emsp; + Tạo và cấu hình inst­ances <br> &emsp; + Triển khai ba ứng dụng mã nguồn mở trên Lightsail: WordPress, PrestaShop, Akaunting <br> &emsp; + Cấu hình mạng / networking: gán static IP cho VM <br> &emsp; + Cấu hình bảo mật ứng dụng <br> &emsp; + Tạo snapshot,backup cho database và instance <br>&emsp; + Dịch chuyển sang instance lớn hơn: tạo snapshot thủ công của instance hiện tại <br>&emsp; + Tạo cảnh báo theo dõi hệ thống                                                                     | 29/09/2025   | 29/09/2025      | <https://000045.awsstudygroup.com/> |
| 3   | - **Triển khai dịch vụ Container AWS Lightsail** <br>&emsp; + Khởi tạo một Lightsail Container Service trên AWS <br>&emsp; + Đưa container image lên Lightsail <br>&emsp; + Tạo Lightsail instance <br>&emsp; + Cài đặt Docker cho Lightsail Instance <br>&emsp; + Build và Push container image lên Lightsail store <br>&emsp; + Triển khai container                                                                                                                                                                                                                                                            | 30/09/2025   | 30/09/2025      | <https://000046.awsstudygroup.com/> |
| 4   | - **Thực hành DynamoDB trên AWS Management Console** <br>&emsp; + Tạo bảng, ghi dữ liệu, đọc dữ liệu, cập nhật, truy vấn <br>&emsp; + Tạo Global secondary index <br>&emsp; + Sử dụng AWS CloudShell <br>&emsp; + Tạo bảng, ghi, đọc, cập nhật, truy vấn dữ liệu <br>&emsp; + Tạo Global secondary index <br>&emsp; + Sử dụng AWS SDK (CRUD) <br>&emsp; + Cấu hình AWS CLI                                                                                                                                                                                                                                        | 01/10/2025   | 01/10/2025      | <https://000060.awsstudygroup.com/> |
| 5   | - **Thực hành Amazon ElastiCache:** <br>&emsp; + Tạo VPC, subnet group và security group cho ElastiCache <br>&emsp; Tạo ElastiCache Cluster (Redis hoặc Memcached) <br>&emsp; + Cấu hình node type, number of nodes, parameter settings <br>&emsp; + Kết nối EC2 → ElastiCache qua private endpoint <br> - Viết code/CLI: Set key/value,Get key/value,Xóa key <br>&emsp; + Tạo replication group, test failover (đối với Redis) <br>&emsp; + Kiểm tra performance khi caching bật/tắt                                                                                                                             | 02/10/2025   | 02/10/2025      | <https://000061.awsstudygroup.com/> |
| 6   | - **Thực hành dịch vụ Networking trên AWS:** <br>&emsp; + Tạo VPC, route table, subnet, Internet Gateway <br>&emsp; + Tạo Security Group & Network ACL <br>&emsp; + Tạo EC2 trong public,private subnet, kết nối SSH <br>&emsp; + Cấu hình Application Load Balancer: Target group, Listener, Health check <br>&emsp; + Triển khai Auto Scaling Group gắn với ALB <br>&emsp; + Thiết lập scaling policies <br>&emsp; + Tạo CloudFront Distribution <br>&emsp; + Cấu hình Behavior rules, Cache TTL <br>&emsp; + Kiểm tra truy cập CDN từ domain CloudFront <br>&emsp; + Kiểm tra tăng tốc truy cập qua CloudFront | 03/10/2025   | 03/10/2025      | <https://000092.awsstudygroup.com/> |

### Kết quả đạt được tuần 4:

- Biết cách triển khai database + VM + ứng dụng hoàn chỉnh trên Lightsail, từ backend đến frontend đủ để vận hành website, e-commerce, ứng dụng doanh nghiệp.
- Hiểu về mô hình dữ liệu NoSQL của DynamoDB: khái niệm table, item, attribute; hiểu Primary Key, Secondary Index, các kiểu dữ liệu được hỗ trợ (scalar, document, set)
- ElastiCache hoạt động như in-memory cache giúp tăng tốc ứng dụng, biết triển khai Redis/Memcached trong VPC
- Nắm vững kiến trúc AWS Networking: VPC, route, IGW, NAT, security layers
