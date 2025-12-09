---
title: "SAM Build"
date: "2025-09-15"
weight: 1
chapter: false
pre: " <b> 5.4.1 </b> "
---

#### Build Project với Maven

Maven sẽ compile Java code và download tất cả dependencies cần thiết.

**Clean**

```powershell
cd excel-import-workshop
mvn clean
```

![alt text](/workshop-fcj/images/5-Workshop/5.4-deploy-backend/5.4.1-sam-build/mvn-clean.png)

**Package application**

```powershell
mvn package
```

Quá trình này sẽ:

1. Download dependencies
2. Compile Java source code
3. Package thành JAR file

![alt text](/workshop-fcj/images/5-Workshop/5.4-deploy-backend/5.4.1-sam-build/mvn-package.png)

#### Build với AWS SAM

SAM CLI sẽ chuẩn bị Lambda deployment packages.

```powershell
sam build
```

Quá trình này sẽ:

1. Đọc `template.yaml`
2. Tìm tất cả Lambda functions
3. Copy compiled code từ `target/` vào `.aws-sam/build/`
4. Tạo deployment packages cho từng function

![alt text](/images/5-Workshop/5.4-deploy-backend/5.4.1-sam-build/sam-build.png)
