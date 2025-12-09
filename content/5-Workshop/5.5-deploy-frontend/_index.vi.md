---
title : "Triển khai Frontend"
date : "2025-09-15"
weight : 5
chapter : false
pre : " <b> 5.5 </b> "
---

#### Cập Nhật File config.js

**Bước 1: Lấy API Gateway Endpoint**

1. Mở CloudFormation Console
2. Tìm stack **excel-import-workshop**
3. Chọn tab **Output**
4. Copy value của **ApiUrl**

![alt text](/images/5-Workshop/5.5-Policy/5.5.1-configure/copy-api-gateway-endpoint.png)

**Bước 2: Thay đổi cấu hình**

1. Vào thư mục **/excel-import-frontend/**
2. Vào thư mục **/excel-import-frontend/src**
3. Mở file **config.js**
4. Thay **APP_API_URL** bằng value của **ApiUrl** vừa copy
5. Save lại

![alt text](/images/5-Workshop/5.5-Policy/5.5.1-configure/config-change.png)

**Bước 3: Build Frontend và tạo S3 Bucket để host Frontend**

Di chuyển vào thư mục Frontend và chạy lần lượt các lệnh sau:

```powershell
cd ./excel-import-frontend/
npm install
npm run build
aws s3 mb s3://workshop-frontend-<ACCOUNT-ID> --region ap-southeast-1
```

![alt text](/images/5-Workshop/5.5-Policy/5.5.1-configure/build-frontend.png)

Sau khi build hoàn tất, thư mục **dist** sẽ được tạo.

![alt text](/images/5-Workshop/5.5-Policy/5.5.1-configure/mb-bucket.png)

**Bước 4: Host Frontend trên S3 Bucket**

1. Vào S3 Bucket Console
2. Chọn Bucket **workshop-frontend-&lt;ACCOUNT-ID&gt;** vừa tạo

![alt text](/images/5-Workshop/5.5-Policy/5.5.1-configure/click-fe-bucket.png)

3. Mở folder **dist** (tạo từ lệnh `npm run build` ở **Bước 3**) nhấn **CTRL + A** để copy toàn bộ **file** và **folder**.
4. Kéo toàn bộ **file** và **folder** đã copy vào phần **Upload** của **Bucket**

![alt text](/images/5-Workshop/5.5-Policy/5.5.1-configure/copy-drag.png)

5. Click **Upload**, after upload success click **Close**

![alt text](/images/5-Workshop/5.5-Policy/5.5.1-configure/click-upload.png)

6. Vào tab **Permissions**
7. Click **Edit** **Block public access (bucket settings)**

![alt text](/images/5-Workshop/5.5-Policy/5.5.1-configure/click-edit-permisson.png)

8. Bỏ chọn **Block public access**

![alt text](/images/5-Workshop/5.5-Policy/5.5.1-configure/unBLock-save.png)

9. Vào **Object Ownership** chuyển thành **ACLs enabled** sau đó **Save**

![alt text](/images/5-Workshop/5.5-Policy/5.5.1-configure/object-owner.png)

1.  Chọn tab **Object** select all **file** và **folder** click **Action** và chọn **Make Public** và **Close**. 

![alt text](/images/5-Workshop/5.5-Policy/5.5.1-configure/make-public.png)

11. Click chọn **Index.html** copy **Object URL** ở tab mới để vào website.

![alt text](/images/5-Workshop/5.5-Policy/5.5.1-configure/object-url.png)
