---
title: "Worklog Tuần 6"
date: 2026-07-27
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6:

- Hoàn thiện chức năng tối ưu hóa hình ảnh trong hệ thống **Automatic Image Optimization System on AWS**.
- Bổ sung các chức năng xử lý ảnh nâng cao như tạo thumbnail, hỗ trợ nhiều định dạng và tính toán thông số sau xử lý.
- Kiểm thử toàn bộ luồng xử lý ảnh kết hợp giữa Amazon S3, AWS Lambda và Amazon DynamoDB.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc                                                                                                                                                                                      | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | -------------- |
| 2   | - Rà soát và hoàn thiện lại logic xử lý ảnh trong AWS Lambda <br> - Kiểm tra quá trình đọc ảnh từ S3 và ghi ảnh sau xử lý <br> - Điều chỉnh cấu hình xử lý ảnh                                 | 27/07/2026   | 27/07/2026      | -              |
| 3   | - Bổ sung chức năng tạo thumbnail cho ảnh <br> - Xây dựng luồng lưu trữ thumbnail trên Amazon S3 <br> - Kiểm tra khả năng truy xuất ảnh thumbnail sau khi xử lý                                | 28/07/2026   | 28/07/2026      | -              |
| 4   | - Mở rộng khả năng xử lý nhiều định dạng hình ảnh: <br>&emsp; + JPEG <br>&emsp; + PNG <br>&emsp; + WEBP <br> - Kiểm tra quá trình chuyển đổi định dạng ảnh                                     | 29/07/2026   | 29/07/2026      | -              |
| 5   | - Bổ sung tính toán các thông số sau khi xử lý: <br>&emsp; + Original size <br>&emsp; + Processed size <br>&emsp; + Compression ratio <br>&emsp; + Processing time                             | 30/07/2026   | 30/07/2026      | -              |
| 6   | - Kiểm thử toàn bộ hệ thống: <br>&emsp; + Upload nhiều ảnh lên S3 <br>&emsp; + Lambda xử lý tự động <br>&emsp; + Kiểm tra ảnh output và thumbnail <br>&emsp; + Kiểm tra metadata trên DynamoDB | 31/07/2026   | 01/08/2026      | -              |

### Kết quả đạt được tuần 6:

- Hoàn thiện chức năng xử lý ảnh tự động trên AWS Lambda.

- Bổ sung khả năng tạo thumbnail cho ảnh sau khi xử lý:
  - Tạo ảnh kích thước nhỏ phục vụ việc xem trước.
  - Lưu trữ thumbnail trên Amazon S3.

- Mở rộng khả năng xử lý nhiều định dạng ảnh:
  - JPEG.
  - PNG.
  - WEBP.

- Hoàn thiện quá trình tối ưu hình ảnh:
  - Resize ảnh theo cấu hình.
  - Giảm dung lượng ảnh.
  - Chuyển đổi định dạng ảnh khi cần thiết.

- Bổ sung tính toán các thông tin phục vụ việc đánh giá hiệu quả tối ưu:
  - Kích thước ảnh ban đầu.
  - Kích thước ảnh sau xử lý.
  - Tỷ lệ giảm dung lượng.
  - Thời gian xử lý.

- Kiểm thử thành công toàn bộ luồng xử lý:
  - Upload ảnh lên Amazon S3.
  - S3 kích hoạt AWS Lambda.
  - Lambda thực hiện tối ưu hình ảnh.
  - Ảnh kết quả và thumbnail được lưu trữ.
  - Metadata được cập nhật vào DynamoDB.

- Hoàn thiện phần chức năng chính của hệ thống **Automatic Image Optimization System on AWS**, sẵn sàng cho giai đoạn theo dõi, bảo mật và hoàn thiện hệ thống.
