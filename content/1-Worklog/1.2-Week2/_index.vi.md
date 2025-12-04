---
title: "Worklog Tuần 2"
date: "2025-09-21"
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---

{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

### Mục tiêu tuần 2:

- Tìm hiểu và triển khai VPC
- Tìm hiểu và triển khai EC2 Instance trong VPC
- Thiết lập Hybrid DNS với Route 53 Resolver

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc                                                                                                                                                                                                                                                                                                                                                                                                                                    | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                      |
| --- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------- |
| 2   | - Triển khai VPC và EC2 Instance <br> - **Thực hành:** <br>&emsp; + Tạo Subnet <br>&emsp; + Tạo Internet Gateway <br>&emsp; + Tạo Route Table <br>&emsp; +Tạo Security Group <br>&emsp; + Kích hoạt VPC Flow Logs <br>&emsp; + Tạo EC2 Instance <br>&emsp; + Kết nối bằng MobaXterm <br>&emsp; + Tạo NAT Gateway <br>&emsp; + Tạo EC2 Instance kết nối Enpoint <br>&emsp; + Tạo CloudWatch                                                   | 15/09/2025   | 15/09/2025      | <https://000003.awsstudygroup.com/> |
| 4   | - Tìm hiểu và thiết lập Hybrid DNS với Route 53 <br> - **Thực hành:** <br>&emsp; + Tạo Key pair <br>&emsp; + Khởi tạo CloudFormation <br>&emsp; + Cấu hình Security Group <br>&emsp; + Kết nối RDGW bằng giao thức RPP <br>&emsp; + Tạo Route 53 Inbound, Outbound <br>&emsp; + Tạo Route 53 Resolver Rules <br>&emsp; + Kết nối vào RD Gateway Server xem kết quả <br>                                                                      | 17/09/2025   | 17/09/2025      | <https://000010.awsstudygroup.com/> |
| 5   | - Tìm hiểu và thiết lập VPC Peering <br> - **Thực hành:** <br>&emsp; + CloudFormation <br>&emsp; + Tạo Security Group <br> &emsp; + Tạo EC2 Instance <br> &emsp; + Ping thử 2 EC2 <br> &emsp; + Cập nhật Network ACL <br> &emsp; + Tạo Peering Connection <br> &emsp; + Cấu hình Route Table <br> &emsp; + Kích hoạt Cross-Peer DNS <br> &emsp; + Ping lại thử 2 EC2                                                                         | 18/09/2025   | 18/09/2025      | <https://000019.awsstudygroup.com/> |
| 6   | - Tìm hiểu về AWS Transit Gateway <br> - **Thực hành:** <br>&emsp; + Tạo keypair <br>&emsp; + Khởi tạo CloudFormation bằng template file <br>&emsp; + Tạo Transit Gateway <br>&emsp; + Tạo Transit Gateway Attachment cho 4 VPC với TG <br>&emsp; + Cấu hình Route Table cho Transit Gateway <br>&emsp; + Thêm Transit Gateway Routes vào VPC Route Tables <br>&emsp; + Kiểm tra kết nối Internet <br>&emsp; + Kiểm tra kết nối giữa các VPC | 19/09/2025   | 19/09/2025      | <https://000020.awsstudygroup.com/> |

### Kết quả đạt được tuần 2:

- Tìm hiểu khái niệm cơ bản về VPC:

  - VPC (Virtual Private Cloud): cho phép khởi chạy một tài nguyên trong mạng ảo mà đã tạo ra
  - Mục đích chính dùng VPC là để phân tách môi trường
  - VPC có thể tạo ra được nhiều mạng ảo và chia thành nhiều mạng ảo con (Subnet)
  - VPC nằm trong 1 Region và và VPC Subnet nằm trong một AZ cụ thể
  - Khi tạo ra VPC -> AWS tự động tạo ra Defaul Route table -> Route table được gán vào subnet

- Tìm hiểu về VPC Endpoint:

  - cho phép kết nối các tài nguyên nằm trong VPC tới các dịch vụ của AWS được hỗ trợ ( AWS PrivateLink ) mà kh cần kết nối Internet
  - Có 2 kiểu VPC Endpoint:
    - Interface Endpoint : sử dụng ENI trong VPC cùng với 1 đchỉ IP Private để kết nới tới dịch vụ
    - Gateway Endpoint : Sử dụng route table để định tiến tới endpoint của dịch vụ hỗ trợ (S3 và Dynamo DB)
  - Muốn kết nối ra bên ngoài bằng public subnet thì sẽ thông qua Internet Gateway
  - Còn private subnet thì sẽ đặt NAT gateway trong public subnet mới có thể kết nối ra bên ngoái

- Triển khai VPC, tạo các Subnet, Internet Gateway, Route table, Security Group
- Triển khai EC2 Instance trong các Subnet

  - Kiểm tra kết nối, két nối bằng SSH cho EC2 Private
  - EC2 kết nối với Endpoint

- Triển Khai CloudWatch cho VPC

- Cài đặt Hybrid DNS với Route 53 Resolver:

  - Tạo Key pair
  - Khởi tạo CloudFormation
  - Kết nối RDGW bằng giao thức RPP (Remote Desktop Protocol)
  - Sử dụng AWS Directory Service để triển khai Microsoft AD
  - Tạo Route 53 Resolver Rules
  - Thử nghiệm kết quả

- Kết nối VPC bằng VPC Peering

  - VPC Peering Connection: là kết nối mạng giữa 2 VPC định tuyến traffic giữa chúng bằng IPv4 hoặc IPv6

  - Networl ACL ( Network Access Control List ) : là lớp bảo mật ở tầng Subnet, có thể chặn traffic trước khi đến Security Group

  - Cross-Peering DNS: là một tính năng của VPC Peering cho phép các tài nguyên bên trong một VPC phân giải DNS của một tài nguyên khác VPC

  - CloudFormation: là dịch vụ giúp tự động tạo, cấu hình, và quản lí hạ tầng AWS bằng mã , thay vì tạo thủ công thì tạo bằng file cấu hình YAML hoặc JSON

- Thực hành được kết nối nhiều VPC bằng Transit Gateway
  - Transit Gateway: là dịch vụ giúp kết nối các mạng VPC và on-premises lại với nhau qua một hub trung tâm
  - Transit Gateway Attachment: giúp kết nối giữa TGW với một mạng cụ thể (như là VPC, VPN)
