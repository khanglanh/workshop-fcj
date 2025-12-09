---
title : "SAM Build"
date : "2025-09-15"
weight : 1
chapter : false
pre : " <b> 5.4.1 </b> "
---

#### Build Project with Maven

Maven will compile the Java code and download all necessary dependencies.

**Clean**


```powershell
cd excel-import-workshop
mvn clean
```
![alt text](/images/5-Workshop/5.4-deploy-backend/5.4.1-sam-build/mvn-clean.png)

**Package application**

```powershell
mvn package
```

This process will:
1. Download dependencies 
2. Compile Java source code
3. Package into a JAR file

![alt text](/images/5-Workshop/5.4-deploy-backend/5.4.1-sam-build/mvn-package.png)

#### Build with AWS SAM

The SAM CLI will prepare Lambda deployment packages.

```powershell
sam build
```

This process will:
1. Read `template.yaml`
2. Find all Lambda functions
3. Copy compiled code from `target/` into `.aws-sam/build/`
4. Create deployment packages for each function

![alt text](/images/5-Workshop/5.4-deploy-backend/5.4.1-sam-build/sam-build.png)