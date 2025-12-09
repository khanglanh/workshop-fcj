---
title : "Preparation Steps"
date :  "2025-09-15" 
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

#### Environment Requirements

To complete this workshop, we need to prepare the following.

**AWS Account:**
- An AWS account (Free Tier is acceptable)
- An IAM user with permissions for the following services:
  - AWS CloudFormation
  - AWS Lambda
  - Amazon API Gateway
  - Amazon S3
  - Amazon DynamoDB
  - Amazon Cognito
  - CloudWatch Logs

**Create AWS Access Key (Assuming you already have an IAM User)**
1. Sign in to AWS
2. Find and select the *IAM* service
3. Select *Users* in the left menu to view the list of IAM Users
4. Find and select the user you previously created
5. Go to the *Security Credentials* section
6. Choose *Create Access Key* to generate a new access key

![alt text](/images/5-Workshop/5.2-prerequisites/create-credential.png)

7. Choose CLI and check Confirmation

![alt text](/images/5-Workshop/5.2-prerequisites/create-access-key.png)

8. Keep the Access Key and Secret Key secure and do not share them with others.

![alt text](/images/5-Workshop/5.2-prerequisites/download-access-key.png)

**AWS CLI:** 

- <a href="https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html" target="_blank" rel="noopener noreferrer">Installation guide</a>

- Check version
```powershell
aws --version
```


![alt text](/images/5-Workshop/5.2-prerequisites/aws-version.png)

---

**AWS SAM CLI:**

- <a href="https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/install-sam-cli.html" target="_blank" rel="noopener noreferrer">Installation guide</a>

- Check version
```powershell
sam --version
```

![alt text](/images/5-Workshop/5.2-prerequisites/sam-version.png)
---

#### AWS CLI Configuration


**Configure credentials**

```powershell
aws configure
```

Enter the Access Key and Secret Key:

![alt text](/images/5-Workshop/5.2-prerequisites/aws-configure.png)

> **Note:** Do not expose your Access Key/Secret Key


#### Clone Workshop Repo

**Clone from Git**

```powershell
git clone https://github.com/Tai-isme/fcj-workshop-s3-notifications
cd fcj-workshop-s3-notifications
```

**Download ZIP**

- <a href="https://github.com/Tai-isme/fcj-workshop-s3-notifications/archive/refs/heads/main.zip" target="_blank" rel="noopener noreferrer">fcj-workshop-s3-notifications.zip</a>

**Project directory structure**

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