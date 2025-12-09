---
title: "Test Application"
date: "2025-12-01"
weight: 6
chapter: false
pre: " <b> 5.6. </b> "
---

#### Test Application

In this section we test the entire workflow: user registration, authentication, uploading sample files and monitoring import status.

1. Sign up and authentication

- On the login screen, click **Sign up**.
  ![Sign up](/workshop-fcj/images/5-Workshop/5.6-test-application/login-page.png)
- Fill in the information and click **Sign up** to create an account.
  ![Sign up Form](/workshop-fcj/images/5-Workshop/5.6-test-application/sign-up.png)
- Enter the **Code** sent to your email and click **Verify Email**.
  ![Enter code](/workshop-fcj/images/5-Workshop/5.6-test-application/code.png)
  ![Verify Email](/workshop-fcj/images/5-Workshop/5.6-test-application/verify.png)
- After verification, log in with the **Email** and **Password** you just created.
  ![Login](/workshop-fcj/images/5-Workshop/5.6-test-application/login.png)

2. Download sample file

- Download the sample import file: [**import-template.xlsx**](/files/5-Workshop/import-template.xlsx)

3. Upload file and import

- Go to the file upload function, select the sample file you just downloaded and upload it.
  ![Upload file](/workshop-fcj/images/5-Workshop/5.6-test-application/upload-file.png)
- After uploading, click **Upload & Import** to start the import process.
  ![Click Upload & Import](/workshop-fcj/images/5-Workshop/5.6-test-application/click-upload-import.png)

4. Monitor progress

- The file will be uploaded to S3 Bucket and trigger Lambda to import data.
  ![Processing](/workshop-fcj/images/5-Workshop/5.6-test-application/processing.png)
- Import status:
  - **Processing** → if no error, it will change to **Completed**.
  - **Processing** → if there is an error, it will change to **Failed** and the system will **automatically rollback**.
    ![Completed](/workshop-fcj/images/5-Workshop/5.6-test-application/completed.png)

5. Verify data after import

- **Check file on S3**

  - Run the following command to check the file you just uploaded:

    ```powershell
    aws s3 ls s3://workshop-excel-imports-<ACCOUNT-ID> --recursive
    ```

  ![alt text](/workshop-fcj/images/5-Workshop/5.6-test-application/s3-check.png)

- **Check table data**

  - Go to **DynamoDB Console** → **Explore items**, select each table to view the data after import.

  ![alt text](/workshop-fcj/images/5-Workshop/5.6-test-application/table-courses.png)
  ![alt text](/workshop-fcj/images/5-Workshop/5.6-test-application/table-jobs.png)
  ![alt text](/workshop-fcj/images/5-Workshop/5.6-test-application/table-student.png)
