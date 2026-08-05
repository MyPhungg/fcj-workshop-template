---
title: "Worklog Tuần 5"
date: 2026-07-20
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần 5:

- Xây dựng chức năng lưu trữ metadata cho hệ thống **Automatic Image Optimization System on AWS**.
- Kết nối AWS Lambda với Amazon DynamoDB để lưu thông tin quá trình xử lý ảnh.
- Theo dõi trạng thái xử lý và các thông tin liên quan đến file ảnh.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc                                                                                                                                                                                                                      | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------ | --------------- | ----------------------------------------- |
| 2   | - Nghiên cứu Amazon DynamoDB phục vụ việc lưu trữ metadata <br> - Xác định thông tin cần lưu trữ: <br>&emsp; + Thông tin file ảnh <br>&emsp; + Trạng thái xử lý <br>&emsp; + Thời gian xử lý <br>&emsp; + Thông tin dung lượng | 20/07/2026   | 20/07/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Tạo DynamoDB Table lưu trữ Image Metadata <br> - Thiết kế cấu trúc dữ liệu: <br>&emsp; + Partition Key <br>&emsp; + Sort Key <br>&emsp; + Các thuộc tính metadata khác                                                       | 21/07/2026   | 21/07/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Cập nhật AWS Lambda Function để kết nối DynamoDB <br> - Cấu hình quyền IAM cho phép Lambda truy cập DynamoDB <br> - Thực hiện ghi dữ liệu metadata sau khi xử lý ảnh hoàn tất                                                | 22/07/2026   | 22/07/2026      | -                                         |
| 5   | - Xây dựng cơ chế cập nhật trạng thái xử lý ảnh: <br>&emsp; + PROCESSING <br>&emsp; + SUCCESS <br>&emsp; + FAILED <br> - Lưu thông tin lỗi khi quá trình xử lý thất bại                                                        | 23/07/2026   | 23/07/2026      | -                                         |
| 6   | - Kiểm tra dữ liệu metadata trên DynamoDB <br> - Kiểm thử luồng xử lý hoàn chỉnh: <br>&emsp; + Upload ảnh <br>&emsp; + Lambda xử lý <br>&emsp; + Lưu ảnh output <br>&emsp; + Lưu metadata                                      | 24/07/2026   | 25/07/2026      | -                                         |

### Kết quả đạt được tuần 5:

- Tạo thành công DynamoDB Table phục vụ việc lưu trữ metadata của ảnh.

- Xây dựng được cấu trúc dữ liệu metadata bao gồm:
  - Thông tin định danh:
    - Batch ID.
    - Processing ID.

  - Thông tin file:
    - Original name.
    - Input bucket.
    - Output bucket.
    - Input key.
    - Output key.

  - Thông tin xử lý:
    - Processing status.
    - Processing time.
    - Error message.

  - Thông tin dung lượng:
    - Original size.
    - Processed size.
    - Compression ratio.

- Kết nối thành công AWS Lambda với DynamoDB để lưu dữ liệu sau quá trình xử lý ảnh.

- Xây dựng cơ chế cập nhật trạng thái xử lý:
  - **PROCESSING:** Lambda đang thực hiện xử lý ảnh.
  - **SUCCESS:** Quá trình xử lý hoàn tất.
  - **FAILED:** Xảy ra lỗi trong quá trình xử lý.

- Kiểm tra dữ liệu được ghi nhận trên DynamoDB sau khi Lambda hoàn thành xử lý.

- Hoàn thiện chức năng quản lý metadata, giúp hệ thống có khả năng theo dõi thông tin và trạng thái của từng ảnh trong quá trình xử lý.
