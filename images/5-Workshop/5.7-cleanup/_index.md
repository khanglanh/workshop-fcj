---
title: "Cleanup Resources"
date: "2025-12-01"
weight: 7
chapter: false
pre: " <b> 5.7. </b> "
---

**1) Delete S3 Buckets Content**

```powershell
# Delete all objects in the bucket (empty)
aws s3 rm s3://workshop-excel-imports-<YOUR-ACCOUNT-ID> --recursive
aws s3 rm s3://workshop-frontend-<YOUR-ACCOUNT-ID> --recursive
```

![Empty buckets](/images/5-Workshop/5.7-cleanup/empty-bucket.png)

**2) Delete S3 Buckets**

After the bucket is empty, delete the bucket using the command:

```powershell
aws s3 rb s3://workshop-excel-imports-<YOUR-ACCOUNT-ID>
aws s3 rb s3://workshop-frontend-<YOUR-ACCOUNT-ID>
```

![Remove buckets](/images/5-Workshop/5.7-cleanup/rb-bucket.png)

**3) Handle `SamCliSourceBucket` created by SAM CLI**

- `SamCliSourceBucket` is a temporary bucket created by AWS SAM CLI to upload source code when running `sam deploy`.
- If this bucket has **Bucket Versioning** enabled, you must manually delete the versioned objects before deleting the bucket.

1. Open AWS Console -> S3 -> select `SamCliSourceBucket` (example name: `aws-sam-cli-managed-default-...`).
2. Go to **Properties** tab -> **Bucket Versioning**.
3. If **Versioning = Enabled**, delete the object versions (or temporarily disable versioning and delete each version) then empty the bucket.
4. After the bucket has no objects (all versions), select **Delete bucket** and confirm.

![Bucket versioning](/images/5-Workshop/5.7-cleanup/versioning.png)

![Managed bucket delete](/images/5-Workshop/5.7-cleanup/managed-bucket.png)

**4) Delete CloudFormation stack (SAM delete)**

```powershell
cd ./excel-import-workshop/
sam delete --stack-name excel-import-workshop --region us-east-1 --no-prompts
```

![SAM delete](/images/5-Workshop/5.7-cleanup/sam-delete.png)
