---
title: "Worklog Tuần 8"
date: 2026-08-05
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8:

- Hoàn thiện hệ thống **Automatic Image Optimization System on AWS**.
- Kiểm tra lại toàn bộ luồng hoạt động của hệ thống sau khi triển khai.
- Tổng hợp tài liệu, kết quả thực hiện và chuẩn bị nội dung báo cáo.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc                                                                                                                                                                                                                  | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | -------------- |
| 2   | - Kiểm tra lại toàn bộ kiến trúc hệ thống <br> - Rà soát các thành phần AWS đã triển khai: <br>&emsp; + Amazon S3 <br>&emsp; + AWS Lambda <br>&emsp; + Amazon DynamoDB <br>&emsp; + Amazon CloudWatch                      | 10/08/2026   | 10/08/2026      | -              |
| 3   | - Kiểm thử toàn bộ quy trình xử lý ảnh: <br>&emsp; + Upload ảnh lên hệ thống <br>&emsp; + S3 nhận file <br>&emsp; + Lambda thực hiện xử lý <br>&emsp; + Lưu ảnh output và thumbnail <br>&emsp; + Lưu metadata vào DynamoDB | 11/08/2026   | 11/08/2026      | -              |
| 4   | - Kiểm tra và đánh giá kết quả xử lý ảnh <br> - Kiểm tra các thông tin metadata: <br>&emsp; + File information <br>&emsp; + Processing status <br>&emsp; + Compression ratio <br>&emsp; + Processing time                  | 12/08/2026   | 12/08/2026      | -              |
| 5   | - Hoàn thiện tài liệu triển khai hệ thống <br> - Tổng hợp các bước cấu hình AWS Service <br> - Bổ sung hình ảnh minh họa và kết quả thực hiện                                                                              | 13/08/2026   | 13/08/2026      | -              |
| 6   | - Chuẩn bị nội dung báo cáo và demo hệ thống <br> - Tổng kết kết quả đạt được trong quá trình thực hiện project                                                                                                            | 14/08/2026   | 15/08/2026      | -              |

### Kết quả đạt được tuần 8:

- Hoàn thiện hệ thống **Automatic Image Optimization System on AWS** với các thành phần chính:
  - Amazon S3:
    - Lưu trữ ảnh đầu vào.
    - Lưu trữ ảnh sau khi tối ưu.
    - Lưu trữ thumbnail.

  - AWS Lambda:
    - Tự động xử lý ảnh khi có file được upload.
    - Thực hiện resize, compression và tạo thumbnail.

  - Amazon DynamoDB:
    - Lưu trữ metadata của quá trình xử lý.
    - Theo dõi trạng thái xử lý ảnh.

  - Amazon CloudWatch:
    - Theo dõi log và hoạt động của Lambda.

- Kiểm thử thành công toàn bộ quy trình xử lý:
  - Người dùng upload ảnh.
  - Ảnh được lưu trên Amazon S3.
  - Lambda được kích hoạt tự động.
  - Ảnh được tối ưu và lưu vào vị trí output.
  - Metadata được ghi nhận vào DynamoDB.

- Kiểm tra và đánh giá các thông tin sau quá trình xử lý:
  - Kích thước ảnh trước và sau tối ưu.
  - Tỷ lệ giảm dung lượng.
  - Thời gian xử lý.
  - Trạng thái xử lý.

- Hoàn thiện tài liệu mô tả kiến trúc và quá trình triển khai hệ thống.

- Chuẩn bị nội dung trình bày, demo và tổng kết kết quả thực hiện trong quá trình xây dựng hệ thống **Automatic Image Optimization System on AWS**.
