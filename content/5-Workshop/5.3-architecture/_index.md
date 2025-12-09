---
title : "Architecture"
date : "2025-09-15"
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

#### System Architecture Overview

The Excel Import system is designed as a **Serverless Event-Driven Architecture**, leveraging AWS managed services to reduce operational overhead and optimize costs.

![alt text](/images/5-Workshop/5.3-architecture/workshop-s3-notifications.png)

#### Details

**Endpoints:**

- POST /register (RegisterFunction)
- POST /confirm (ConfirmFunction)
- POST /login (LoginFunction)
- POST /logout (LogoutFunction)
- POST /upload-url (GenerateUploadUrlFunction)
- GET /import/jobs (ListImportJobsFunction)
- GET /jobs/{jobId} (GetJobStatusFunction)


**Core Processing Function**

![alt text](/images/5-Workshop/5.3-architecture/core-function.png)

**Process Flow:**
   1. Get file from S3 (event.Records[0].s3)
   2. Parse Excel using Apache POI
   3. Validate each row (email format, required fields)
   4. Batch write to DynamoDB (25 items/batch)
   5. Update ImportJob status & statistics
Output: Updated ImportJob record
Tables: StudentsTable, CoursesTable, ImportJobsTable


**Amazon S3 (File Storage):** Storage for user-imported files.
![alt text](/images/5-Workshop/5.3-architecture/import-bucket.png)  