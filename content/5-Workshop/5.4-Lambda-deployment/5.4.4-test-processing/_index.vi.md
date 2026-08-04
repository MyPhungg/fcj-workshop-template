---
title: "Kiểm tra quá trình xử lý ảnh bằng AWS Lambda"
date: 2026-08-04
weight: 4
chapter: false
pre: " <b> 5.4.4 </b> "
---

# Kiểm tra quá trình xử lý ảnh bằng AWS Lambda

Sau khi hoàn thành việc tạo Lambda Function, cấu hình source code và kết nối S3 Event Trigger, bước này thực hiện kiểm tra toàn bộ pipeline xử lý ảnh của hệ thống **Automatic Image Optimization System on AWS**.

Mục tiêu kiểm tra:

- Xác nhận Lambda được kích hoạt khi có ảnh mới upload lên S3.
- Kiểm tra quá trình tối ưu hóa hình ảnh.
- Kiểm tra ảnh kết quả được lưu vào Output Bucket.
- Kiểm tra metadata được ghi vào DynamoDB.
- Kiểm tra log thực thi trên CloudWatch.

---

# 1. Chuẩn bị file ảnh kiểm tra

Chuẩn bị một file ảnh mẫu:

```
sample-image.jpg
```

File ảnh được sử dụng để mô phỏng hành động upload của người dùng.

Ví dụ:

```
sample-image.jpg
```

Thông tin:

```
Format:
JPEG

Purpose:
Lambda Image Processing Test
```

---

# 2. Upload ảnh vào Input Bucket

Truy cập:

```
Amazon S3 Console
```

Chọn:

```
auto-images-input-bucket
```

Upload ảnh vào thư mục:

```
uploads/
```

Cấu trúc sau khi upload:

```
auto-images-input-bucket
│
└── uploads/
    |
    └── sample-image.jpg
```

![upload-test-image](/images/5-Workshop/5.4-Lambda/test-processing/upload-image.png)

---

# 3. Kiểm tra Lambda được kích hoạt

Sau khi file được upload, Amazon S3 sẽ gửi sự kiện:

```
Object Created Event
```

đến Lambda Function:

```
image-optimizer-lambda
```

Luồng xử lý:

```
Amazon S3
    |
    |
Object Created Event
    |
    v
image-optimizer-lambda
    |
    |
Process Image
```

---

# 4. Kiểm tra Lambda Execution Logs

Truy cập:

```
AWS Lambda Console
```

Chọn:

```
image-optimizer-lambda
```

Vào:

```
Monitor
    |
    +--> View CloudWatch logs
```

Kiểm tra log thực thi.

Ví dụ:

```
START RequestId: xxx

Downloading image from S3...

Optimizing image...

Generating thumbnail...

Uploading processed image...

Saving metadata to DynamoDB...

END RequestId: xxx
```

![cloudwatch-log](/images/5-Workshop/5.4-Lambda/test-processing/cloudwatch-log.png)

---

# 5. Kiểm tra ảnh đã được tối ưu hóa

Sau khi Lambda xử lý thành công, truy cập Output Bucket:

```
auto-images-output-bucket
```

Kiểm tra cấu trúc:

```
auto-images-output-bucket
│
└── optimized/
    |
    └── user001/
        |
        └── batch-id/
            |
            └── sample-image.webp
```

Kết quả:

- Ảnh được chuyển đổi sang format tối ưu.
- Kích thước file giảm so với ảnh gốc.
- Chất lượng ảnh được duy trì theo cấu hình.

![output-image](/images/5-Workshop/5.4-Lambda/test-processing/output-image.png)

---

# 6. Kiểm tra Thumbnail được tạo

Lambda Function sẽ tạo thêm ảnh thumbnail phục vụ hiển thị nhanh trên giao diện.

Cấu trúc:

```
auto-images-output-bucket
│
└── thumbnails/
    |
    └── user001/
        |
        └── batch-id/
            |
            └── sample-image.webp
```

Thumbnail có kích thước nhỏ hơn ảnh gốc, giúp giảm thời gian tải khi hiển thị danh sách ảnh.

![thumbnail-result](/images/5-Workshop/5.4-Lambda/test-processing/thumbnail.png)

---

# 7. Kiểm tra dữ liệu trong DynamoDB

Sau khi xử lý hoàn tất, Lambda ghi thông tin metadata vào DynamoDB.

Truy cập:

```
Amazon DynamoDB Console
```

Chọn table:

```
ImageMetadata
```

Kiểm tra item được tạo:

Ví dụ:

```json
{
  "batchId": "xxxx-xxxx",
  "processingId": "xxxx-xxxx",
  "originalName": "sample-image.jpg",
  "status": "SUCCESS",
  "format": "WEBP",
  "originalSize": 204800,
  "processedSize": 51200
}
```

Các thông tin được lưu:

- Tên file gốc.
- Bucket nguồn.
- Bucket kết quả.
- Trạng thái xử lý.
- Kích thước trước và sau tối ưu.
- Thời gian xử lý.

![dynamodb-result](/images/5-Workshop/5.4-Lambda/test-processing/dynamodb-result.png)

---

# 8. Kiểm tra trạng thái xử lý lỗi

Để đảm bảo hệ thống xử lý đúng lỗi, có thể kiểm tra trường hợp:

- File không đúng định dạng.
- File bị lỗi.
- Lambda không có quyền truy cập S3.

Khi xảy ra lỗi, DynamoDB sẽ lưu:

```
status:
FAILED

errorMessage:
<error description>
```

CloudWatch Logs cũng ghi lại thông tin lỗi để phục vụ việc theo dõi.

---

# 9. Kiểm tra toàn bộ luồng hệ thống

Sau khi test thành công, toàn bộ pipeline hoạt động như sau:

```
                 User
                  |
                  |
            Upload Image
                  |
                  v
      auto-images-input-bucket
                  |
                  |
        Object Created Event
                  |
                  v
       image-optimizer-lambda
                  |
        +---------+---------+
        |                   |
        v                   v
 Optimize Image       Generate Thumbnail
        |                   |
        +---------+---------+
                  |
                  v
     auto-images-output-bucket
                  |
                  v
          DynamoDB Metadata
                  |
                  v
          CloudWatch Logs
```

---

# 10. Kết quả

Quá trình kiểm tra Lambda Function hoàn tất thành công.

Kết quả đạt được:

- Lambda được kích hoạt tự động từ S3 Event.
- Ảnh được tối ưu hóa thành công.
- Thumbnail được tạo tự động.
- Ảnh kết quả được lưu vào Output Bucket.
- Metadata được lưu vào DynamoDB.
- Log xử lý được ghi nhận trên CloudWatch.

Hệ thống **Automatic Image Optimization System on AWS** đã hoàn thành pipeline xử lý ảnh tự động.

```
S3 Upload
    |
    v
Lambda Processing
    |
    v
Optimized Image + Thumbnail
    |
    v
DynamoDB Metadata
```
