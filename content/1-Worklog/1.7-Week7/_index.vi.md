---
title: "Worklog Tuần 7"
date: 2026-08-03
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7:

- Triển khai các chức năng theo dõi và kiểm tra hoạt động của hệ thống **Automatic Image Optimization System on AWS**.
- Nghiên cứu cách sử dụng Amazon CloudWatch để giám sát AWS Lambda.
- Kiểm tra quyền truy cập và các cấu hình bảo mật cho các tài nguyên AWS trong hệ thống.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc                                                                                                                                                                                       | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Tìm hiểu Amazon CloudWatch phục vụ monitoring hệ thống <br> - Kiểm tra Lambda Logs: <br>&emsp; + Execution log <br>&emsp; + Error log <br>&emsp; + Runtime information                        | 03/08/2026   | 03/08/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Theo dõi hoạt động của AWS Lambda sau khi xử lý ảnh <br> - Kiểm tra các thông tin: <br>&emsp; + Lambda invocation <br>&emsp; + Execution time <br>&emsp; + Error message                      | 04/08/2026   | 04/08/2026      | -                                         |
| 4   | - Nghiên cứu Amazon SNS phục vụ thông báo hệ thống <br> - Tìm hiểu cách kết hợp SNS với các dịch vụ AWS khác khi xảy ra sự kiện hoặc lỗi                                                        | 05/08/2026   | 05/08/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Kiểm tra và cập nhật IAM Permission cho hệ thống <br> - Kiểm tra quyền truy cập giữa các thành phần: <br>&emsp; + Lambda → S3 <br>&emsp; + Lambda → DynamoDB <br>&emsp; + User → AWS Resource | 06/08/2026   | 06/08/2026      | -                                         |
| 6   | - Kiểm tra các cấu hình bảo mật hệ thống <br> - Nghiên cứu AWS KMS trong việc bảo vệ dữ liệu <br> - Kiểm thử lại toàn bộ luồng xử lý sau khi hoàn thiện monitoring và security                  | 07/08/2026   | 08/08/2026      | -                                         |

### Kết quả đạt được tuần 7:

- Hiểu được vai trò của Amazon CloudWatch trong việc giám sát hệ thống AWS.

- Có khả năng kiểm tra và phân tích Lambda Logs:
  - Theo dõi quá trình Lambda được kích hoạt.
  - Kiểm tra thông tin thực thi.
  - Phát hiện và phân tích lỗi trong quá trình xử lý.

- Kiểm tra được trạng thái hoạt động của hệ thống thông qua các thông tin:
  - Lambda invocation.
  - Execution time.
  - Error message.

- Nghiên cứu cách sử dụng Amazon SNS để hỗ trợ gửi thông báo khi hệ thống phát sinh sự kiện hoặc lỗi.

- Kiểm tra và điều chỉnh quyền truy cập IAM cho các thành phần trong hệ thống:
  - AWS Lambda có quyền đọc và ghi dữ liệu trên Amazon S3.
  - AWS Lambda có quyền lưu metadata vào Amazon DynamoDB.
  - Đảm bảo các tài nguyên AWS được truy cập đúng theo mục đích.

- Tìm hiểu cơ chế bảo mật dữ liệu bằng AWS KMS.

- Hoàn thiện việc kiểm tra monitoring và security, giúp hệ thống có khả năng theo dõi hoạt động, phát hiện lỗi và quản lý quyền truy cập tài nguyên tốt hơn.
