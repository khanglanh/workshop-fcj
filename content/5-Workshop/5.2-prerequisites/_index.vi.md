---
title: "Các bước chuẩn bị"
date: "2025-09-15"
weight: 2
chapter: false
pre: " <b> 5.2. </b> "
---

#### Yêu Cầu Môi Trường

Để hoàn thành workshop này, chúng ta cần chuẩn bị.

**AWS Account:**

- Tài khoản AWS có thể sử dụng Free Tier
- IAM user có quyền với các services:
  - AWS CloudFormation
  - AWS Lambda
  - Amazon API Gateway
  - Amazon S3
  - Amazon DynamoDB
  - Amazon Cognito
  - CloudWatch Logs

**Tạo AWS Access Key (Giả sử bạn đã có IAM User)**

1. Đăng nhập vào AWS
2. Tìm và chọn dịch vụ _IAM_
3. Chọn mục _Users_ ở menu bên trái để xem danh sách các IAM User
4. Tìm và chọn người dùng mà bạn đã tạo trước đó
5. Tìm đến mục _Security Credentials_
6. Chọn _Create Access Key_ để tạo một khóa truy cập mới

![alt text](/workshop-fcj/images/5-Workshop/5.2-Prerequisite/create-credential.png)

7. Chọn CLI và tick Confirmation

![alt text](/workshop-fcj/images/5-Workshop/5.2-Prerequisite/create-access-key.png)

8. Giữ Access key và Secret key an toàn và không chia sẻ cho người khác.

![alt text](/workshop-fcj/images/5-Workshop/5.2-Prerequisite/download-access-key.png)

**AWS CLI:**

- <a href="https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html" target="_blank" rel="noopener noreferrer">Hướng dẫn cài đặt</a>

- Kiểm tra phiên bản

```powershell
aws --version
```

![alt text](/workshop-fcj/images/5-Workshop/5.2-Prerequisite/aws-version.png)

---

**AWS SAM CLI:**

- <a href="https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/install-sam-cli.html" target="_blank" rel="noopener noreferrer">Hướng dẫn cài đặt</a>

- Kiểm tra phiên bản

```powershell
sam --version
```

## ![alt text](images/5-Workshop/5.2-Prerequisite/sam-version.png)

#### Cấu Hình AWS CLI

**Cấu hình credentials**

```powershell
aws configure
```

Điền Access key và Secret key:

![alt text](images/5-Workshop/5.2-Prerequisite/aws-configure.png)

> **Lưu ý:** Không để lộ Access Key/Secret Key

#### Clone Workshop Repo

**Clone từ Git**

```powershell
git clone https://github.com/Tai-isme/fcj-workshop-s3-notifications
cd fcj-workshop-s3-notifications
```

**Download ZIP**

- <a href="https://github.com/Tai-isme/fcj-workshop-s3-notifications/archive/refs/heads/main.zip" target="_blank" rel="noopener noreferrer">fcj-workshop-s3-notifications.zip</a>

**Cấu trúc thư mục**

```
📦fcj-workshop-s3-notifications
 ┣ 📂excel-import-frontend
 ┃ ┣ 📂src
 ┃ ┣ 📜package.json
 ┃ ┗ 📜vite.config.js
 ┗ 📂excel-import-workshop
 ┃ ┣ 📂src
 ┃ ┣ 📜pom.xml
 ┃ ┗ 📜template.yaml
```
