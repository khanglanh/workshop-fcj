---
title: "Dọn dẹp tài nguyên"
date: "2025-12-01"
weight: 7
chapter: false
pre: " <b> 5.7. </b> "
---

**1) Xoá nội dung của S3 Buckets**

```powershell
# Xóa tất cả object trong bucket (empty)
aws s3 rm s3://workshop-excel-imports-<YOUR-ACCOUNT-ID> --recursive
aws s3 rm s3://workshop-frontend-<YOUR-ACCOUNT-ID> --recursive
```

![Empty buckets](/images/5-Workshop/5.7-cleanup/empty-bucket.png)

**2) Xoá S3 Buckets**

Sau khi bucket đã rỗng, xoá bucket bằng lệnh:

```powershell
aws s3 rb s3://workshop-excel-imports-<YOUR-ACCOUNT-ID>
aws s3 rb s3://workshop-frontend-<YOUR-ACCOUNT-ID>
```

![Remove buckets](/images/5-Workshop/5.7-cleanup/rb-bucket.png)

**3) Xử lý `SamCliSourceBucket` do SAM CLI tạo**

- `SamCliSourceBucket` là bucket tạm do AWS SAM CLI tạo để upload mã nguồn khi `sam deploy`.
- Nếu bucket này có **Bucket Versioning** bật (Enabled), bạn phải xóa thủ công các phiên bản (versioned objects) trước khi xoá bucket.

1. Mở AWS Console -> S3 -> chọn `SamCliSourceBucket` (tên ví dụ: `aws-sam-cli-managed-default-...`).
2. Chuyển sang tab **Properties** -> **Bucket Versioning**.
3. Nếu **Versioning = Enabled**, xóa các phiên bản object (hoặc tạm thời tắt versioning và xóa từng phiên bản) rồi empty bucket.
4. Sau khi bucket không còn object (cả version), chọn **Delete bucket** và xác nhận.

![Bucket versioning](/images/5-Workshop/5.7-cleanup/versioning.png)

![Managed bucket delete](/images/5-Workshop/5.7-cleanup/managed-bucket.png)

**4) Xóa CloudFormation stack (SAM delete)**

```powershell
cd ./excel-import-workshop/
sam delete --stack-name excel-import-workshop --region us-east-1 --no-prompts
```

![SAM delete](/images/5-Workshop/5.7-cleanup/sam-delete.png)