---
title: "Worklog Tuần 2"
date: 2026-06-29
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu tuần 2:

- Tìm hiểu các dịch vụ AWS cần thiết cho hệ thống **Automatic Image Optimization System on AWS**.
- Nghiên cứu cách hoạt động của Amazon S3, AWS Lambda và Amazon DynamoDB.
- Thực hành các thao tác cơ bản với các dịch vụ AWS phục vụ cho quá trình triển khai hệ thống.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc                                                                                                                                                                                                                                    | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Tìm hiểu Amazon S3: <br>&emsp; + Bucket <br>&emsp; + Object <br>&emsp; + Key <br>&emsp; + Region <br> - Nghiên cứu vai trò của S3 trong việc lưu trữ dữ liệu trên AWS                                                                      | 29/06/2026   | 29/06/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Thực hành với Amazon S3: <br>&emsp; + Tạo S3 Bucket <br>&emsp; + Upload object lên Bucket <br>&emsp; + Download object <br>&emsp; + Kiểm tra quyền truy cập tài nguyên                                                                     | 30/06/2026   | 30/06/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Tìm hiểu AWS Lambda: <br>&emsp; + Serverless Computing <br>&emsp; + Lambda Function <br>&emsp; + Runtime <br>&emsp; + Event Trigger <br> - Nghiên cứu cách Lambda có thể xử lý dữ liệu tự động                                             | 01/07/2026   | 01/07/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Tìm hiểu Amazon DynamoDB: <br>&emsp; + NoSQL Database <br>&emsp; + Table <br>&emsp; + Partition Key <br>&emsp; + Sort Key <br>&emsp; + Item <br> - Nghiên cứu khả năng lưu trữ metadata cho hệ thống                                       | 02/07/2026   | 02/07/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Nghiên cứu mô hình kết hợp các dịch vụ AWS: <br>&emsp; + S3 lưu trữ hình ảnh <br>&emsp; + Lambda xử lý ảnh tự động <br>&emsp; + DynamoDB lưu metadata <br> - Xác định các dịch vụ phù hợp cho hệ thống Automatic Image Optimization System | 03/07/2026   | 04/07/2026      | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 2:

- Hiểu được vai trò của Amazon S3 trong việc lưu trữ dữ liệu trên AWS.

- Có khả năng thực hiện các thao tác cơ bản với S3:
  - Tạo Bucket.
  - Upload và quản lý Object.
  - Hiểu cấu trúc Key trong S3.
  - Kiểm tra quyền truy cập tài nguyên.

- Nắm được cách hoạt động của AWS Lambda:
  - Lambda Function.
  - Runtime.
  - Event-driven execution.
  - Trigger từ các dịch vụ AWS khác.

- Hiểu được cách sử dụng Amazon DynamoDB:
  - Cách tổ chức dữ liệu dạng NoSQL.
  - Partition Key và Sort Key.
  - Lưu trữ thông tin dạng Item.

- Xác định được kiến trúc dịch vụ AWS phù hợp cho hệ thống:
  - Amazon S3 dùng để lưu trữ ảnh đầu vào và đầu ra.
  - AWS Lambda đảm nhiệm xử lý tối ưu hình ảnh.
  - Amazon DynamoDB lưu trữ metadata và trạng thái xử lý.

- Có kiến thức nền tảng để bắt đầu thiết kế và triển khai hệ thống **Automatic Image Optimization System on AWS**.
