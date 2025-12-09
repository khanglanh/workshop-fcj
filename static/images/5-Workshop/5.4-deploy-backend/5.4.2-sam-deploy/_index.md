---
title : "SAM Deploy"
date : "2025-09-15"
weight : 2
chapter : false
pre : " <b> 5.4.2 </b> "
---

#### Deploy with AWS SAM

SAM CLI will package the code and deploy the entire infrastructure to AWS through CloudFormation.


#### Deploy

There are 2 ways to deploy the application using SAM:

- **Method 1 — Create S3 Bucket Manually**

```powershell
aws s3 mb s3://demo-workshop-be-<YOUR-ID-ACCOUNT> --region ap-southeast-1
```

![Create S3 bucket](/images/5-Workshop/5.4-deploy-backend/5.4.2-sam-deploy/mb-bucket.png)

```powershell
sam deploy --s3-bucket <bucket-name-just-created> --stack-name <stack-name> --region ap-southeast-1
```

- **Method 2 — Use `--guided` (recommended for first time)**

```powershell
sam deploy --guided
```

To keep it simple and avoid creating a bucket manually, we will use **Method 2**. `--guided` will ask for parameters (stack name, region, permissions, etc.) and save the configuration to **samconfig.toml** so next time you only need to run `sam deploy`.

#### SAM will ask some guided questions

![alt text](/images/5-Workshop/5.4-deploy-backend/5.4.2-sam-deploy/guided-question.png)

When running `sam deploy --guided`, SAM will ask for some parameters to configure (for example):

1. **Stack Name [excel-import-workshop]**: Enter the stack name (or leave blank to use the current project name).
2. **AWS Region [ap-southeast-1]**: Enter Region (or leave blank to use **ap-southeast-1**).
3. **Parameter Environment [dev]**: Enter environment (default is **dev** if left blank).
4. **Confirm changes before deploy [y/N]**: Enter **y** to review changes before deploying.
5. **Allow SAM CLI IAM role creation [y/N]**: Enter **y** to allow SAM to create IAM roles for Lambda.
6. **Disable rollback [y/N]**: Enter **n** to enable rollback if deployment fails (recommended **n**).
7. **Save arguments to configuration file [y/N]**: Enter **y** to save the configuration to **samconfig.toml** (so next time you only need to run `sam deploy`).

If you choose **y**, SAM will continue asking for the configuration file name (default is **samconfig.toml**) and environment:

- **SAM configuration file [samconfig.toml]**: samconfig.toml
- **SAM configuration environment [default]**: default

In this example I chose **n** to not save the configuration.
#### Deployment Process

**Preparing CloudFormation**

![alt text](/images/5-Workshop/5.4-deploy-backend/5.4.2-sam-deploy/phase-1.png)

**CloudFormation Change Set**

SAM will display the list of resources to be created:

![alt text](/images/5-Workshop/5.4-deploy-backend/5.4.2-sam-deploy/phase-2.png)

**Confirm deploy:**
Enter: **y** to deploy

![alt text](/images/5-Workshop/5.4-deploy-backend/5.4.2-sam-deploy/changeset-created.png)

**CloudFormation Execution**

![alt text](/images/5-Workshop/5.4-deploy-backend/5.4.2-sam-deploy/resource-create.png)


**CloudFormation Execution Success**

![alt text](/images/5-Workshop/5.4-deploy-backend/5.4.2-sam-deploy/success-deploy.png)

---

#### If you have deployed once with `--guided` and chose **y** at save configuration file:

Then the next deployment only needs:

```powershell
sam build
sam deploy
```
SAM will read the config from **samconfig.toml**.


#### Verify Created Resources

1. Check CloudFormation Stack
- Open CloudFormation Console
- Find stack **excel-import-workshop**
- Stack status should be: **CREATE_COMPLETE**

![alt text](/images/5-Workshop/5.4-deploy-backend/5.4.2-sam-deploy/check-stack-status.png)

2. Check Lambda
- Open Lambda Console
- Select **Functions**

![alt text](/images/5-Workshop/5.4-deploy-backend/5.4.2-sam-deploy/check-function.png)

3. Check API Gateway
- Open API Gateway Console
- Select **api**

![alt text](/images/5-Workshop/5.4-deploy-backend/5.4.2-sam-deploy/check-api-gateway.png)
![alt text](/images/5-Workshop/5.4-deploy-backend/5.4.2-sam-deploy/api-gateway-resource.png)

4. Check S3 Bucket
- Open S3 Console
- Select Bucket **workshop-excel-imports**

![alt text](/images/5-Workshop/5.4-deploy-backend/5.4.2-sam-deploy/s3-bucket.png)

5. Check User pool
- Open Cognito Console
- Select **ExcelWorkshopUsers**

![alt text](/images/5-Workshop/5.4-deploy-backend/5.4.2-sam-deploy/user-pool.png)

**All resources have been deployed successfully and completely.**
