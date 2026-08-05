---
title: "Nhật ký công việc"
date: 2026-08-04
weight: 1
chapter: false
pre: " <b> 1. </b> "
---

Trong quá trình thực hiện chương trình thực tập, em đã hoàn thành công việc trong vòng **8 tuần** từ ngày **22/06/2026 đến 15/08/2026**.

Trong thời gian này, các công việc được thực hiện bao gồm tìm hiểu nền tảng AWS, nghiên cứu các dịch vụ Cloud cần thiết, thực hành triển khai các dịch vụ AWS cơ bản và áp dụng vào việc xây dựng hệ thống **Automatic Image Optimization System on AWS**.

Quá trình thực hiện được chia thành các giai đoạn:

- **Giai đoạn 1:** Tìm hiểu kiến thức nền tảng về AWS, làm quen với AWS Console, AWS CLI và các dịch vụ cơ bản.
- **Giai đoạn 2:** Nghiên cứu kiến trúc hệ thống xử lý ảnh tự động và triển khai các thành phần AWS cần thiết.
- **Giai đoạn 3:** Xây dựng chức năng xử lý ảnh bằng AWS Lambda, lưu trữ bằng Amazon S3 và quản lý metadata bằng DynamoDB.
- **Giai đoạn 4:** Hoàn thiện monitoring, security, kiểm thử hệ thống và chuẩn bị tài liệu báo cáo.

Nội dung công việc trong từng tuần như sau:

**Tuần 1:** [Tìm hiểu AWS Cloud và các dịch vụ cơ bản trong AWS](1.1-week1/)

- Làm quen với nền tảng AWS Cloud.
- Tìm hiểu các nhóm dịch vụ chính:
  - Compute
  - Storage
  - Database
  - Networking
- Tạo AWS Free Tier Account.
- Cấu hình AWS CLI và thực hành thao tác với AWS.

**Tuần 2:** [Nghiên cứu các dịch vụ AWS phục vụ hệ thống xử lý ảnh](1.2-week2/)

- Tìm hiểu Amazon S3:
  - Bucket
  - Object
  - Permission
  - Storage management
- Tìm hiểu AWS Lambda:
  - Serverless computing
  - Function
  - Trigger
- Tìm hiểu DynamoDB:
  - Table
  - Partition Key
  - Sort Key
- Nghiên cứu mô hình kết hợp S3, Lambda và DynamoDB.

**Tuần 3:** [Thiết kế kiến trúc hệ thống Automatic Image Optimization System](1.3-week3/)

- Phân tích yêu cầu của hệ thống.
- Thiết kế kiến trúc xử lý ảnh tự động.
- Xác định vai trò của các AWS services:
  - Amazon S3
  - AWS Lambda
  - Amazon DynamoDB
  - Amazon CloudWatch
  - Amazon SNS
  - IAM
  - AWS KMS
- Thiết kế luồng upload, xử lý và lưu trữ ảnh.

**Tuần 4:** [Triển khai Amazon S3 và AWS Lambda xử lý ảnh](1.4-week4/)

- Tạo và cấu hình S3 Bucket phục vụ lưu trữ ảnh.
- Cấu hình S3 Event Trigger cho Lambda.
- Triển khai Lambda Function xử lý ảnh.
- Nghiên cứu sử dụng Python Pillow để:
  - Resize ảnh
  - Compression ảnh
  - Chuyển đổi định dạng ảnh
- Kiểm thử quá trình upload và xử lý ảnh tự động.

**Tuần 5:** [Xây dựng chức năng lưu trữ metadata bằng DynamoDB](1.5-week5/)

- Thiết kế DynamoDB Table lưu thông tin metadata.
- Xây dựng schema lưu trữ:
  - Batch ID
  - Processing ID
  - File information
  - Processing status
  - Processing time
  - Compression ratio
- Kết nối Lambda với DynamoDB.
- Kiểm tra dữ liệu metadata sau khi xử lý ảnh.

**Tuần 6:** [Hoàn thiện chức năng tối ưu hóa hình ảnh](1.6-week6/)

- Hoàn thiện logic xử lý ảnh bằng Python Pillow.
- Bổ sung chức năng tạo thumbnail.
- Hỗ trợ xử lý nhiều định dạng ảnh:
  - JPEG
  - PNG
  - WEBP
- Tính toán các thông số:
  - Original size
  - Processed size
  - Compression ratio
  - Processing time
- Kiểm thử toàn bộ luồng xử lý ảnh.

**Tuần 7:** [Triển khai Monitoring và Security cho hệ thống](1.7-week7/)

- Theo dõi Lambda execution logs bằng Amazon CloudWatch.
- Kiểm tra trạng thái xử lý của hệ thống.
- Cấu hình SNS để gửi thông báo khi xảy ra lỗi.
- Kiểm tra IAM Permission.
- Nghiên cứu các cơ chế bảo mật:
  - IAM Role
  - KMS Encryption

**Tuần 8:** [Hoàn thiện hệ thống và chuẩn bị báo cáo](1.8-Week8/)

- Kiểm tra lại toàn bộ hệ thống Automatic Image Optimization System on AWS.
- Kiểm thử quy trình:
  - Upload ảnh
  - Lambda xử lý
  - Lưu ảnh output
  - Lưu metadata
- Hoàn thiện tài liệu triển khai.
- Chuẩn bị nội dung demo và báo cáo kết quả thực hiện.
