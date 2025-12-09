---
title : "SAM Deploy"
date : "2025-09-15"
weight : 2
chapter : false
pre : " <b> 5.4.2 </b> "
---

#### Deploy với AWS SAM

SAM CLI sẽ package code và deploy toàn bộ infrastructure lên AWS thông qua CloudFormation.


#### Deploy

Có 2 cách deploy ứng dụng bằng SAM:

- **Cách 1 — Tự tạo S3 Bucket**

```powershell
aws s3 mb s3://demo-workshop-be-<YOUR-ID-ACCOUNT> --region ap-southeast-1
```

![Tạo S3 bucket](/images/5-Workshop/5.4-deploy-backend/5.4.2-sam-deploy/mb-bucket.png)

```powershell
sam deploy --s3-bucket <tên-bucket-vừa-tạo> --stack-name <tên-stack> --region ap-southeast-1
```

- **Cách 2 — Sử dụng `--guided` (khuyến nghị cho lần đầu)**

```powershell
sam deploy --guided
```

Để đơn giản và tránh phải tạo bucket thủ công, chúng ta sẽ sử dụng **Cách 2**. `--guided` sẽ hỏi các tham số (stack name, region, permissions, v.v.) rồi lưu cấu hình vào **samconfig.toml** để lần sau chỉ cần chạy `sam deploy`.

#### SAM sẽ hỏi một số câu hỏi hướng dẫn

![alt text](/images/5-Workshop/5.4-deploy-backend/5.4.2-sam-deploy/guided-question.png)

Khi chạy `sam deploy --guided`, SAM sẽ hỏi một số tham số để cấu hình (ví dụ):

1. **Stack Name [excel-import-workshop]**: Nhập tên stack (hoặc để trống để dùng tên project hiện tại).
2. **AWS Region [ap-southeast-1]**: Nhập Region (hoặc để trống để dùng **ap-southeast-1**).
3. **Parameter Environment [dev]**: Nhập environment (mặc định là **dev** nếu để trống).
4. **Confirm changes before deploy [y/N]**: Nhập **y** để xem lại thay đổi trước khi deploy.
5. **Allow SAM CLI IAM role creation [y/N]**: Nhập **y** để cho phép SAM tạo IAM roles cho Lambda.
6. **Disable rollback [y/N]**: Nhập **n** để bật rollback nếu deploy thất bại (khuyến nghị **n**).
7. **Save arguments to configuration file [y/N]**: Nhập **y** để lưu cấu hình vào **samconfig.toml** (để lần sau chỉ cần chạy `sam deploy`).

Nếu chọn **y**, SAM sẽ tiếp tục hỏi tên file cấu hình (mặc định là **samconfig.toml**) và môi trường:

- **SAM configuration file [samconfig.toml]**: samconfig.toml
- **SAM configuration environment [default]**: default

Trong ví dụ này mình chọn **n** để không lưu cấu hình.
#### Quá Trình Deploy

**Preparing CloudFormation**

![alt text](/images/5-Workshop/5.4-deploy-backend/5.4.2-sam-deploy/phase-1.png)

**CloudFormation Change Set**

SAM sẽ hiển thị danh sách resources sẽ được tạo:

![alt text](/images/5-Workshop/5.4-deploy-backend/5.4.2-sam-deploy/phase-2.png)

**Confirm deploy:**
Nhập: **y** để deploy

![alt text](/images/5-Workshop/5.4-deploy-backend/5.4.2-sam-deploy/changeset-created.png)

**CloudFormation Execution**

![alt text](/images/5-Workshop/5.4-deploy-backend/5.4.2-sam-deploy/resource-create.png)


**CloudFormation Execution Success**

![alt text](/images/5-Workshop/5.4-deploy-backend/5.4.2-sam-deploy/success-deploy.png)

---

#### Nếu đã deploy một lần với `--guided` và chọn **y** ở save configuration file:

Thì lần deploy tiếp theo chỉ cần:

```powershell
sam build
sam deploy
```
SAM sẽ đọc config từ **samconfig.toml**.


#### Kiểm Tra Resources đã tạo

1. Kiểm Tra CloudFormation Stack
- Mở CloudFormation Console
- Tìm stack **excel-import-workshop**
- Status stack phải là: **CREATE_COMPLETE**

![alt text](/images/5-Workshop/5.4-deploy-backend/5.4.2-sam-deploy/check-stack-status.png)

2. Kiểm tra Lambda
- Mở Lambda Console
- Chọn **Functions**

![alt text](/images/5-Workshop/5.4-deploy-backend/5.4.2-sam-deploy/check-function.png)

3. Kiểm tra API Gateway
- Mở API Gateway Console
- Chọn **api**

![alt text](/images/5-Workshop/5.4-deploy-backend/5.4.2-sam-deploy/check-api-gateway.png)
![alt text](/images/5-Workshop/5.4-deploy-backend/5.4.2-sam-deploy/api-gateway-resource.png)

4. Kiểm tra S3 Bucket
- Mở S3 Console
- Chọn Bucket **workshop-excel-imports**

![alt text](/images/5-Workshop/5.4-deploy-backend/5.4.2-sam-deploy/s3-bucket.png)

5. Kiểm tra User pool
- Mở Cognito Console
- Chọn **ExcelWorkshopUsers**

![alt text](/images/5-Workshop/5.4-deploy-backend/5.4.2-sam-deploy/user-pool.png)

**Các resource đã được deploy thành công và đầy đủ.**
