---
title: "Event 3"
date: "2025-11-17"
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---

# Bài thu hoạch “DevOps on AWS”

### Mục Đích Của Sự Kiện

- Cung cấp kiến thức toàn diện về DevOps và cách áp dụng trên nền tảng AWS
- Hiểu tư duy DevOps (DevOps mindset), văn hóa và nguyên tắc cốt lõi
- Trải nghiệm thực tế xây dựng CI/CD pipeline bằng các dịch vụ AWS
- Nắm vững Infrastructure as Code (IaC) với CloudFormation và CDK
- Tìm hiểu các dịch vụ container, giám sát hệ thống và best practices cho DevOps hiện đại

---

### Danh Sách Diễn Giả

- **Dinh Le Hoang Anh** - Instructor
- **Van Hoang Kha** - Instructor
- **Nguyen Khanh Phuc Thinh** - Instructor

---

### Nội Dung Nổi Bật

## **Morning Session (8:30 AM – 12:00 PM)**

---

### **Welcome & DevOps Mindset (8:30 – 9:00 AM)**

- Tổng kết buổi AI/ML session trước đó
- Giới thiệu **văn hóa và tư duy DevOps**
- Lợi ích của DevOps và các **key metrics** quan trọng:
  - DORA Metrics
  - MTTR (Mean Time to Recovery)
  - Deployment Frequency

---

### **AWS DevOps Services – CI/CD Pipeline (9:00 – 10:30 AM)**

- **Source Control** với AWS CodeCommit, Git Strategies:
  - GitFlow
  - Trunk-based development
- **Build & Test** với AWS CodeBuild
- **Deployment** qua AWS CodeDeploy:
  - Blue/Green
  - Canary
  - Rolling updates
- **Orchestration** bằng AWS CodePipeline
- **Demo thực tế**: CI/CD pipeline from end-to-end

---

### **Break (10:30 – 10:45 AM)**

---

### **Infrastructure as Code (IaC) (10:45 AM – 12:00 PM)**

- **CloudFormation**: templates, stacks, drift detection
- **AWS CDK**: constructs, patterns tái sử dụng, hỗ trợ đa ngôn ngữ
- **Demo** triển khai hạ tầng bằng CloudFormation & CDK
- Thảo luận: Nên chọn công cụ IaC nào và khi nào?

---

### **Lunch Break (12:00 – 1:00 PM)** _(Tự túc)_

---

## **Afternoon Session (1:00 PM – 5:00 PM)**

### **Container Services on AWS (1:00 – 2:30 PM)**

- Kiến thức nền tảng về Docker và microservices
- **Amazon ECR**: lưu trữ image, scanning, lifecycle policies
- So sánh và sử dụng **Amazon ECS & Amazon EKS**
- **AWS App Runner**: triển khai container đơn giản nhất
- **Demo & Case Study**: so sánh các phương pháp triển khai microservices

---

### **Break (2:30 – 2:45 PM)**

---

### **Monitoring & Observability (2:45 – 4:00 PM)**

- **Amazon CloudWatch**: metrics, logs, alarms, dashboards
- **AWS X-Ray**: tracing, performance insights
- **Demo full-stack observability setup**
- Best practices: alerting, dashboards, on-call rotation

---

### **DevOps Best Practices & Case Studies (4:00 – 4:45 PM)**

- Chiến lược triển khai: Feature Flags, A/B Testing
- Automated testing kết hợp CI/CD
- Incident management & postmortems
- Case studies: DevOps tại startup vs enterprise

---

### **Q&A & Wrap-up (4:45 – 5:00 PM)**

- Career pathways trong lĩnh vực DevOps
- Lộ trình chứng chỉ AWS dành cho DevOps

---

### Những Gì Học Được

#### **Tư Duy DevOps**

- Tư duy DevOps giúp tăng tốc độ phát triển và nâng cao chất lượng sản phẩm
- Hiểu vai trò của collaboration, automation và measurement trong DevOps
- Nắm rõ các chỉ số đánh giá hiệu quả DevOps (DORA)

---

#### **Kỹ Thuật CI/CD**

- Thiết kế Git workflow hợp lý theo quy mô team
- Build – Test – Deploy tự động bằng CodeCommit, CodeBuild, CodeDeploy, CodePipeline
- Lựa chọn chiến lược deployment phù hợp (Blue/Green, Canary, Rolling)

---

#### **Infrastructure as Code**

- Viết template CloudFormation và triển khai hạ tầng tự động
- Sử dụng CDK để định nghĩa hạ tầng bằng ngôn ngữ lập trình quen thuộc
- Tối ưu IaC bằng reusable constructs và patterns

---

#### **Containerization & Microservices**

- Hiểu rõ kiến trúc container và microservices
- So sánh ECS, EKS và App Runner để chọn giải pháp phù hợp
- Đẩy, scan và quản lý container images trong Amazon ECR

---

#### **Monitoring & Observability**

- Thiết lập giám sát toàn diện với CloudWatch
- Dùng X-Ray để trace request và phân tích hiệu năng
- Thiết kế quy trình cảnh báo và trực on-call khoa học

---

### Ứng Dụng Vào Công Việc

- Xây dựng CI/CD pipeline tự động hóa cho dự án
- Áp dụng IaC để quản lý hạ tầng minh bạch và dễ tái sử dụng
- Lựa chọn công nghệ container phù hợp với nhu cầu dự án
- Thiết lập observability giúp giảm thời gian xử lý sự cố
- Áp dụng DevOps best practices vào quy trình vận hành thực tế

---

### Trải nghiệm trong event

#### **Học hỏi từ chuyên gia AWS**

- Các diễn giả cung cấp cái nhìn thực tế về DevOps hiện đại
- Các demo chi tiết giúp tôi hiểu rõ cách vận hành hệ thống DevOps trong thực tế

#### **Trải nghiệm kỹ thuật thực tế**

- Trực tiếp quan sát toàn bộ CI/CD pipeline trên AWS
- Làm quen với IaC và container orchestration qua các ví dụ cụ thể

#### **Ứng dụng công cụ DevOps chuẩn AWS**

- Thấy rõ cách AWS hỗ trợ đầy đủ toolset phục vụ DevOps từ đầu đến cuối
- Học được cách đánh giá và lựa chọn công cụ phù hợp theo nhu cầu dự án

#### **Bài học rút ra**

- DevOps không chỉ là công cụ mà là **văn hóa làm việc**
- Automate càng nhiều, rủi ro càng thấp và tốc độ càng nhanh
- Observability và incident management là nền tảng của vận hành hiện đại

### Một số hình ảnh khi tham gia sự kiện

![alt text](/workshop-fcj/images/ngay17/anh1.png)
![alt text](/workshop-fcj/images/ngay17/anh2.png)
![alt text](/workshop-fcj/images/ngay17/anh3.png)

> Tổng thể, workshop “DevOps on AWS” mang lại cho tôi cái nhìn toàn diện về DevOps hiện đại, quy trình CI/CD, IaC, container hóa và giám sát hệ thống, giúp tôi tự tin hơn khi áp dụng DevOps vào dự án thực tế.
