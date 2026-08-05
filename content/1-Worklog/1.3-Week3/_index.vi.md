---
title: "Worklog Tuần 3"
date: 2026-07-06
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần 3:

- Phân tích yêu cầu và thiết kế kiến trúc cho hệ thống **Automatic Image Optimization System on AWS**.
- Xác định vai trò của từng dịch vụ AWS được sử dụng trong hệ thống.
- Chuẩn bị các thành phần cần thiết trước khi triển khai hệ thống.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc                                                                                                                                                                                                                                                       | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Phân tích yêu cầu hệ thống Automatic Image Optimization System <br> - Xác định mục tiêu chính của hệ thống: <br>&emsp; + Nhận ảnh từ người dùng <br>&emsp; + Tự động tối ưu hình ảnh <br>&emsp; + Lưu trữ ảnh sau xử lý <br>&emsp; + Theo dõi thông tin xử lý | 06/07/2026   | 06/07/2026      | -                                         |
| 3   | - Thiết kế kiến trúc tổng thể của hệ thống <br> - Xây dựng luồng xử lý: <br>&emsp; User Upload Image <br>&emsp; → Amazon S3 <br>&emsp; → AWS Lambda <br>&emsp; → Output Storage <br>&emsp; → DynamoDB Metadata                                                  | 07/07/2026   | 07/07/2026      | -                                         |
| 4   | - Nghiên cứu vai trò của các dịch vụ AWS trong hệ thống: <br>&emsp; + Amazon S3 <br>&emsp; + AWS Lambda <br>&emsp; + Amazon DynamoDB <br>&emsp; + Amazon CloudWatch <br>&emsp; + Amazon SNS <br>&emsp; + IAM <br>&emsp; + AWS KMS                               | 08/07/2026   | 08/07/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Thiết kế luồng xử lý hình ảnh: <br>&emsp; + Upload ảnh lên hệ thống <br>&emsp; + Kích hoạt Lambda thông qua S3 Event Trigger <br>&emsp; + Xử lý và tối ưu ảnh <br>&emsp; + Lưu ảnh kết quả và metadata                                                        | 09/07/2026   | 09/07/2026      | -                                         |
| 6   | - Chuẩn bị môi trường triển khai hệ thống <br> - Kiểm tra quyền truy cập AWS <br> - Xác định các tài nguyên AWS cần tạo cho quá trình phát triển                                                                                                                | 10/07/2026   | 11/07/2026      | -                                         |

### Kết quả đạt được tuần 3:

- Phân tích được yêu cầu của hệ thống **Automatic Image Optimization System on AWS**.

- Hoàn thiện kiến trúc tổng thể của hệ thống:
  - Người dùng tải ảnh lên hệ thống.
  - Ảnh được lưu trữ trên Amazon S3.
  - AWS Lambda được kích hoạt để thực hiện quá trình xử lý.
  - Ảnh sau khi tối ưu được lưu trữ lại trên S3.
  - Metadata của quá trình xử lý được lưu trong Amazon DynamoDB.

- Xác định được vai trò của từng AWS service:
  - **Amazon S3:**
    - Lưu trữ ảnh đầu vào.
    - Lưu trữ ảnh sau khi tối ưu.

  - **AWS Lambda:**
    - Thực hiện xử lý ảnh tự động khi có sự kiện upload.

  - **Amazon DynamoDB:**
    - Lưu thông tin metadata của ảnh.
    - Theo dõi trạng thái xử lý.

  - **Amazon CloudWatch:**
    - Theo dõi log và hoạt động của Lambda.

  - **Amazon SNS:**
    - Gửi thông báo khi có sự kiện hoặc lỗi xảy ra.

  - **IAM và AWS KMS:**
    - Quản lý quyền truy cập và bảo mật tài nguyên.

- Xây dựng được luồng xử lý chính của hệ thống, làm cơ sở để triển khai các thành phần AWS trong các tuần tiếp theo.

- Chuẩn bị được môi trường và kế hoạch triển khai hệ thống.
