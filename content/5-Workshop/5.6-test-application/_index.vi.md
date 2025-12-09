---
title: "Test Ứng Dụng"
date: "2025-12-01"
weight: 6
chapter: false
pre: " <b> 5.6. </b> "
---

#### Test Application

Trong phần này chúng ta kiểm tra toàn bộ luồng hoạt động: đăng ký người dùng, xác thực, upload file mẫu và theo dõi trạng thái import.

1. Đăng ký và xác thực

- Tại màn hình đăng nhập, click **Sign up**.
  ![Đăng ký](/images/5-Workshop/5.6-test-application/login-page.png)
- Điền thông tin và click **Sign up** để tạo tài khoản.
  ![Form Sign up](/images/5-Workshop/5.6-test-application/sign-up.png)
- Nhập **Code** được gửi qua email rồi click **Verify Email**.
  ![Nhập code](/images/5-Workshop/5.6-test-application/code.png)
  ![Verify Email](/images/5-Workshop/5.6-test-application/verify.png)
- Sau khi verify, đăng nhập bằng **Email** và **Password** vừa tạo.
  ![Đăng nhập](/images/5-Workshop/5.6-test-application/login.png)

2. Tải file mẫu

- Tải file import mẫu: [**import-template.xlsx**](/files/5-Workshop/import-template.xlsx)

3. Upload file và import

- Vào chức năng upload file, chọn file mẫu vừa tải về và upload.
  ![Upload file](/images/5-Workshop/5.6-test-application/upload-file.png)
- Sau khi upload, click **Upload & Import** để bắt đầu quá trình import.
  ![Click Upload & Import](/images/5-Workshop/5.6-test-application/click-upload-import.png)

4. Theo dõi tiến trình

- File sẽ được đưa lên S3 Bucket và kích hoạt Lambda để import dữ liệu.
  ![Processing](/images/5-Workshop/5.6-test-application/processing.png)
- Trạng thái import:
  - **Processing** → nếu không lỗi sẽ chuyển **Completed**.
  - **Processing** → nếu có lỗi sẽ chuyển **Failed** và hệ thống sẽ **tự động rollback**.
    ![Completed](/images/5-Workshop/5.6-test-application/completed.png)

5. Kiểm tra dữ liệu sau import

- **Kiểm tra file trên S3**

  - Chạy lệnh sau để kiểm tra file vừa upload:

    ```powershell
    aws s3 ls s3://workshop-excel-imports-<ACCOUNT-ID> --recursive
    ```

  ![alt text](/images/5-Workshop/5.6-test-application/s3-check.png)

- **Kiểm tra dữ liệu các tables**

  - Vào **DynamoDB Console** → **Explore items**, chọn từng table để xem dữ liệu sau import.

  ![alt text](/images/5-Workshop/5.6-test-application/table-courses.png)
  ![alt text](/images/5-Workshop/5.6-test-application/table-jobs.png)
  ![alt text](/images/5-Workshop/5.6-test-application/table-student.png)
