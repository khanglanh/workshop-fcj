---
title: "Event 4"
date: "2025-11-29"
weight: 4
chapter: false
pre: " <b> 4.4. </b> "
---

# Bài thu hoạch “AWS Well-Architected Security Pillar Workshop”

### Mục Đích Của Sự Kiện

- Cung cấp cái nhìn toàn diện về **Security Pillar** trong AWS Well-Architected Framework
- Trang bị kiến thức nền tảng về bảo mật hạ tầng cloud theo 5 trụ cột chính
- Hướng dẫn các best practices trong xây dựng hệ thống an toàn, tuân thủ và khả năng phục hồi cao
- Thực hành các công cụ bảo mật AWS như IAM, GuardDuty, CloudTrail, KMS, Secrets Manager
- Nâng cao tư duy thiết kế bảo mật theo các mô hình: **Least Privilege, Zero Trust, Defense in Depth**

---

### Danh Sách Diễn Giả

- **Van Hoang Kha** - Instructor
- **Nguyen Tuan Thinh** - Instructor

---

### Nội Dung Nổi Bật

## **Opening & Security Foundation (8:30 – 8:50 AM)**

- Vai trò của **Security Pillar** trong Well-Architected Framework
- Ba nguyên tắc bảo mật cốt lõi:
  - **Least Privilege**
  - **Zero Trust**
  - **Defense in Depth**
- **Shared Responsibility Model** và các tình huống áp dụng
- Xu hướng và **top threats** trong môi trường cloud tại Việt Nam

---

## **Pillar 1 — Identity & Access Management (8:50 – 9:30 AM)**

### Modern IAM Architecture

- IAM Users, Roles, Policies – tránh long-term credentials
- **IAM Identity Center**: SSO, permission sets
- **Service Control Policies (SCP)** và permission boundaries trong multi-account
- MFA, credential rotation, Access Analyzer
- **Mini Demo:** kiểm tra & simulate IAM policy

---

## **Pillar 2 — Detection (9:30 – 9:55 AM)**

### Detection & Continuous Monitoring

- **CloudTrail** (organization-level), **GuardDuty**, **Security Hub**
- Logging đa tầng: VPC Flow Logs, ALB Logs, S3 Access Logs
- Alerting + automation với **EventBridge Rules**
- **Detection-as-Code:** quản lý detection rules dưới dạng IaC

---

### Coffee Break (9:55 – 10:10 AM)

---

## **Pillar 3 — Infrastructure Protection (10:10 – 10:40 AM)**

### Network & Workload Security

- VPC segmentation, private/public subnet strategies
- **Security Groups vs NACLs**: mô hình áp dụng trong thực tế
- WAF + Shield + Network Firewall
- Workload protection cho: EC2, ECS/EKS

---

## **Pillar 4 — Data Protection (10:40 – 11:10 AM)**

### Encryption, Keys & Secrets

- **AWS KMS**: key policy, grants, key rotation
- Encryption at-rest & in-transit:
  - S3, EBS, RDS, DynamoDB
- Secrets Manager & Parameter Store: secret rotation patterns
- Data classification & guardrails trong doanh nghiệp

---

## **Pillar 5 — Incident Response (11:10 – 11:40 AM)**

### IR Playbook & Automation

- IR lifecycle theo AWS
- Playbooks mô phỏng thực tế:
  - Compromised IAM key
  - Public S3 bucket exposure
  - EC2 malware detection
- Snapshot, isolate instance, evidence collection
- **Auto-response** bằng Lambda và Step Functions

---

## **Wrap-Up & Q&A (11:40 – 12:00 PM)**

- Tổng kết **5 pillars** của Security Framework
- Common pitfalls và thực tế triển khai tại doanh nghiệp Việt Nam
- Roadmap học tập: Security Specialty, Solutions Architect Professional

---

### Những Gì Học Được

#### **Kiến Thức Nền Tảng Về Cloud Security**

- Hiểu rõ vai trò và tầm quan trọng của Security Pillar
- Nắm cách thiết kế hệ thống dựa trên Zero Trust & Least Privilege
- Nhận thức các mối đe dọa phổ biến trong môi trường cloud tại Việt Nam

---

#### **Identity & Access Management**

- Thiết kế kiến trúc IAM hiện đại với Identity Center và SCP
- Hạn chế long-term credentials và áp dụng MFA bắt buộc
- Sử dụng Access Analyzer để đánh giá rủi ro quyền truy cập

---

#### **Monitoring & Detection**

- Kích hoạt đầy đủ logging và theo dõi đa tầng
- Tối ưu phát hiện bất thường với GuardDuty & Security Hub
- Kết hợp EventBridge để tự động hóa cảnh báo và phản hồi

---

#### **Infrastructure & Data Protection**

- Thiết kế VPC segmentation giúp tăng độ an toàn cho workload
- Sử dụng encryption at-rest & in-transit theo best practice
- Quản lý secrets an toàn với Secrets Manager và Parameter Store

---

#### **Incident Response**

- Hiểu IR lifecycle và biết cách xây dựng playbook hiệu quả
- Tự động hóa một phần IR bằng Lambda/Step Functions
- Biết cách cô lập, thu thập chứng cứ và điều tra sự cố

---

### Ứng Dụng Vào Công Việc

- Có thể thiết kế hệ thống AWS theo chuẩn Well-Architected Security Pillar
- Áp dụng IAM best practices vào dự án (MFA, no long-term credentials, SCP…)
- Thiết lập logging, monitoring và guardrails cho hệ thống nội bộ
- Thực hành xây dựng playbook để rút ngắn thời gian phản ứng sự cố
- Triển khai encryption & secret rotation theo đúng khuyến nghị của AWS

---

### Trải nghiệm trong event

#### **Học hỏi từ chuyên gia AWS**

- Diễn giả truyền đạt nội dung dễ hiểu, có ví dụ thực tế tại doanh nghiệp Việt Nam
- Học được cách phân tích rủi ro và bố trí bảo mật đa lớp

#### **Trải nghiệm kỹ thuật thực tế**

- Demo IAM policy simulation giúp tôi hiểu rõ cách đánh giá quyền
- Quan sát logging & detection workflow cho phép tôi hình dung rõ hoạt động của hệ thống bảo mật

#### **Ứng dụng công cụ bảo mật AWS**

- Sử dụng GuardDuty, Security Hub, KMS và Secrets Manager trong mô hình demo
- Cách bật logging toàn hệ thống và tổ chức cảnh báo hợp lý

#### **Bài học rút ra**

- Bảo mật là trách nhiệm liên tục, không phải cấu hình một lần
- Identity là lớp bảo mật đầu tiên và quan trọng nhất
- Một hệ thống tốt cần có khả năng phát hiện, phản hồi và khắc phục nhanh chóng

---

### Một số hình ảnh khi tham gia sự kiện

![alt text](/workshop-fcj/images/ngay29/anh1.png)
![alt text](/workshop-fcj/images/ngay29/anh2.png)
![alt text](/workshop-fcj/images/ngay29/anh3.png)

> Tổng thể, workshop “AWS Well-Architected Security Pillar” mang đến góc nhìn sâu sắc về thiết kế hệ thống an toàn trên AWS, giúp tôi hình thành tư duy bảo mật chuẩn mực và có thể áp dụng ngay vào công việc.
