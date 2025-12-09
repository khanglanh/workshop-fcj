---
title: "Kiến trúc"
date: "2025-09-15"
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---

#### Kiến Trúc Tổng Quan

Hệ thống Excel Import được thiết kế theo mô hình **Serverless Event-Driven Architecture**, tận dụng các managed services của AWS để giảm thiểu operational overhead và tối ưu chi phí.

![alt text](images/5-Workshop/5.3-architecture/workshop-s3-notifications.png)

#### Chi tiết

**Endpoints:**

- POST /register (RegisterFunction)
- POST /confirm (ConfirmFunction)
- POST /login (LoginFunction)
- POST /logout (LogoutFunction)
- POST /upload-url (GenerateUploadUrlFunction)
- GET /import/jobs (ListImportJobsFunction)
- GET /jobs/{jobId} (GetJobStatusFunction)

**Core Processing Function**

![alt text](images/5-Workshop/5.3-architecture/core-function.png)

**Process Flow:**

1.  Get file từ S3 (event.Records[0].s3)
2.  Parse Excel bằng Apache POI
3.  Validate từng row (email format, required fields)
4.  Batch write vào DynamoDB (25 items/batch)
5.  Update ImportJob status & statistics
    Output: Updated ImportJob record
    Tables: StudentsTable, CoursesTable, ImportJobsTable

**Amazon S3 (File Storage):** Storage lưu trữ các file user import.
![alt text](images/5-Workshop/5.3-architecture/import-bucket.png)
