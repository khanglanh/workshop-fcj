---
title: "Deploy Frontend"
date: "2025-09-15"
weight: 5
chapter: false
pre: " <b> 5.5 </b> "
---

#### Update config.js File

**Step 1: Get API Gateway Endpoint**

1. Open CloudFormation Console
2. Find stack **excel-import-workshop**
3. Select **Output** tab
4. Copy value of **ApiUrl**

![alt text](/images/5-Workshop/5.5-deploy-frontend/5.5.1-configure/copy-api-gateway-endpoint.png)

**Step 2: Change Configuration**

1. Go to **/excel-import-frontend/** directory
2. Go to **/excel-import-frontend/src** directory
3. Open **config.js** file
4. Replace **APP_API_URL** with the value of **ApiUrl** copied earlier
5. Save it

![alt text](/images/5-Workshop/5.5-deploy-frontend/5.5.1-configure/config-change.png)

**Step 3: Build Frontend and Create S3 Bucket to Host Frontend**

Navigate to the Frontend directory and run the following commands in order:

```powershell
cd ./excel-import-frontend/
npm install
npm run build
aws s3 mb s3://workshop-frontend-<ACCOUNT-ID> --region ap-southeast-1
```

![alt text](/images/5-Workshop/5.5-deploy-frontend/5.5.1-configure/build-frontend.png)

After the build is complete, the **dist** folder will be created.

![alt text](/images/5-Workshop/5.5-deploy-frontend/5.5.1-configure/mb-bucket.png)

**Step 4: Host Frontend on S3 Bucket**

1. Go to S3 Bucket Console
2. Select Bucket **workshop-frontend-&lt;ACCOUNT-ID&gt;** just created

![alt text](/images/5-Workshop/5.5-deploy-frontend/5.5.1-configure/click-fe-bucket.png)

3. Open **dist** folder (created from `npm run build` command in **Step 3**), press **CTRL + A** to copy all **files** and **folders**.
4. Drag all **files** and **folders** copied into the **Upload** section of the **Bucket**

![alt text](/images/5-Workshop/5.5-deploy-frontend/5.5.1-configure/copy-drag.png)

5. Click **Upload**, after upload success click **Close**

![alt text](/images/5-Workshop/5.5-deploy-frontend/5.5.1-configure/click-upload.png)

6. Go to **Permissions** tab
7. Click **Edit** **Block public access (bucket settings)**

![alt text](/images/5-Workshop/5.5-deploy-frontend/5.5.1-configure/click-edit-permisson.png)

8. Uncheck **Block public access**

![alt text](/images/5-Workshop/5.5-deploy-frontend/5.5.1-configure/unBLock-save.png)

9. Go to **Object Ownership** change to **ACLs enabled** then **Save**

![alt text](/images/5-Workshop/5.5-deploy-frontend/5.5.1-configure/object-owner.png)

10. Select **Object** tab select all **files** and **folders** click **Action** and select **Make Public** and **Close**.

![alt text](/images/5-Workshop/5.5-deploy-frontend/5.5.1-configure/make-public.png)

11. Click select **Index.html** copy **Object URL** in the new tab to access the website.

![alt text](/images/5-Workshop/5.5-deploy-frontend/5.5.1-configure/object-url.png)
