---
title: "Worklog Tuần 4"
date: 2026-07-13
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4:

- Triển khai các thành phần lưu trữ và xử lý chính cho hệ thống **Automatic Image Optimization System on AWS**.
- Cấu hình Amazon S3 để lưu trữ hình ảnh đầu vào, đầu ra.
- Xây dựng AWS Lambda Function để thực hiện quá trình tối ưu hình ảnh tự động.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc                                                                                                                                                                           | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Tạo và cấu hình Amazon S3 Bucket phục vụ hệ thống <br>&emsp; + Bucket lưu ảnh đầu vào <br>&emsp; + Bucket lưu ảnh sau xử lý <br> - Kiểm tra cấu trúc lưu trữ Object trong S3      | 13/07/2026   | 13/07/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Nghiên cứu cơ chế S3 Event Trigger <br> - Cấu hình sự kiện khi có ảnh mới được upload lên S3 <br> - Kết nối S3 với AWS Lambda Function                                            | 14/07/2026   | 14/07/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Triển khai AWS Lambda Function xử lý ảnh <br> - Cấu hình Lambda Runtime Python <br> - Thiết lập Environment Variables cho Lambda Function <br> - Kiểm tra Lambda Execution Role   | 15/07/2026   | 15/07/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Xây dựng logic xử lý hình ảnh bằng Python Pillow <br>&emsp; + Đọc ảnh từ S3 <br>&emsp; + Resize hình ảnh <br>&emsp; + Tối ưu dung lượng ảnh <br>&emsp; + Lưu ảnh sau xử lý lên S3 | 16/07/2026   | 16/07/2026      | -                                         |
| 6   | - Kiểm thử quá trình xử lý ảnh tự động <br>&emsp; + Upload ảnh lên S3 <br>&emsp; + Kiểm tra Lambda được kích hoạt <br>&emsp; + Kiểm tra ảnh sau tối ưu được lưu trữ thành công      | 17/07/2026   | 18/07/2026      | -                                         |

### Kết quả đạt được tuần 4:

- Triển khai thành công các tài nguyên Amazon S3 phục vụ hệ thống:
  - Bucket lưu trữ ảnh đầu vào.
  - Bucket lưu trữ ảnh sau quá trình tối ưu.

- Cấu hình được cơ chế S3 Event Trigger để tự động kích hoạt Lambda khi có ảnh mới được upload.

- Triển khai thành công AWS Lambda Function xử lý ảnh:
  - Cấu hình Python Runtime.
  - Thiết lập quyền truy cập thông qua IAM Role.
  - Cấu hình các biến môi trường phục vụ quá trình xử lý.

- Xây dựng được chức năng xử lý ảnh bằng Python Pillow:
  - Đọc file ảnh từ S3.
  - Thực hiện resize ảnh theo kích thước cấu hình.
  - Tối ưu dung lượng ảnh.
  - Upload ảnh đã xử lý lên S3.

- Kiểm thử thành công luồng xử lý cơ bản:
  - Người dùng upload ảnh lên S3.
  - S3 phát sinh sự kiện.
  - Lambda được kích hoạt.
  - Ảnh sau xử lý được lưu vào S3 Output Bucket.

- Hoàn thiện phần xử lý chính của hệ thống, làm nền tảng để tiếp tục xây dựng chức năng lưu trữ metadata và theo dõi trạng thái xử lý trong các tuần tiếp theo.
