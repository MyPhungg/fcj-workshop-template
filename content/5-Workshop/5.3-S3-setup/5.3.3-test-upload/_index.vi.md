---
title: "Kiểm tra quá trình upload và xử lý ảnh"
date: 2026-08-04
weight: 3
chapter: false
pre: " <b> 5.3.3 </b> "
---

# Kiểm tra quá trình upload và xử lý ảnh

Sau khi hoàn thành việc tạo S3 Bucket và cấu hình S3 Trigger cho AWS Lambda, bước tiếp theo là kiểm tra toàn bộ quy trình xử lý ảnh của hệ thống.

Quá trình kiểm tra bao gồm:

1. Upload ảnh vào Input Bucket.
2. Kiểm tra S3 Trigger kích hoạt Lambda.
3. Kiểm tra ảnh sau khi tối ưu trong Output Bucket.
4. Kiểm tra metadata được lưu trong DynamoDB.

Luồng kiểm tra:

```
Upload Image
      |
      v
Input S3 Bucket
      |
      v
S3 Event Notification
      |
      v
AWS Lambda
      |
      +----------------+
      |                |
      v                v
Output S3 Bucket   DynamoDB
(Optimized Image)  (Metadata)
```

---

# 1. Upload ảnh vào Input Bucket

Truy cập:

[Amazon S3 Console](https://s3.console.aws.amazon.com/s3/)

Chọn bucket:

```
auto-images-input-bucket
```

Sau đó chọn:

```
Upload
```

để tải ảnh kiểm thử lên hệ thống.

![upload-image](/images/5-Workshop/5.3-S3/upload-image.png)

---

# 2. Chuẩn bị file ảnh kiểm thử

Chọn một file ảnh có định dạng được hệ thống hỗ trợ:

```
.jpg
.jpeg
.png
.webp
```

Ví dụ:

```
test-image.jpg
```

File ảnh được upload với cấu trúc:

```
auto-images-input-bucket

uploads/
 └── user001/
      └── test-image.jpg
```

Trong quá trình upload, Backend sẽ đính kèm metadata cần thiết cho Lambda:

```
batchId
userId
originalName
```

Các thông tin này được Lambda sử dụng để phân loại ảnh sau khi xử lý.

---

# 3. Kiểm tra S3 Trigger hoạt động

Sau khi upload thành công, Amazon S3 sẽ phát sinh sự kiện:

```
Object Created
```

Sự kiện này sẽ kích hoạt Lambda function:

```
image-optimizer-lambda
```

Kiểm tra tại:

```
AWS Lambda
 → Monitor
 → View CloudWatch logs
```

![lambda-log](/images/5-Workshop/5.3-S3/lambda-log.png)

Nếu Lambda hoạt động thành công, CloudWatch Logs sẽ hiển thị các bước:

```
Downloading image from S3
Processing image
Generating thumbnail
Uploading optimized image
Saving metadata to DynamoDB
Processing completed
```

---

# 4. Kiểm tra ảnh sau khi xử lý

Sau khi Lambda hoàn thành, truy cập Output Bucket:

```
auto-images-output-bucket
```

Kết quả mong đợi:

```
auto-images-output-bucket

optimized/
 └── user001/
      └── batchId/
            └── test-image.webp


thumbnails/
 └── user001/
      └── batchId/
            └── test-image.webp
```

![output-image](/images/5-Workshop/5.3-S3/output-image.png)

Kiểm tra:

- Ảnh đã được chuyển đổi sang định dạng mong muốn.
- Kích thước file giảm so với ảnh gốc.
- Thumbnail được tạo thành công.

---

# 5. Kiểm tra dữ liệu trong DynamoDB

Sau khi xử lý hoàn tất, Lambda lưu thông tin vào DynamoDB.

Truy cập:

```
Amazon DynamoDB
 → Tables
 → ImageMetadata
```

Một record mẫu:

```
{
    "batchId": "batch-001",
    "processingId": "uuid-processing-id",
    "userId": "user001",
    "originalName": "test-image.jpg",
    "status": "SUCCESS",
    "originalSize": 5242880,
    "processedSize": 1048576,
    "compressionRatio": 80,
    "processingTimeMs": 2500
}
```

![dynamodb-result](/images/5-Workshop/5.3-S3/dynamodb-result.png)

---

# 6. Kiểm tra trạng thái xử lý lỗi

Ngoài trường hợp thành công, hệ thống cũng xử lý lỗi khi:

- File không phải định dạng ảnh.
- File bị lỗi hoặc không thể đọc.
- Lambda không có quyền truy cập S3.
- Không thể ghi dữ liệu vào DynamoDB.

Khi xảy ra lỗi, DynamoDB lưu trạng thái:

```
status = FAILED
```

kèm thông tin:

```
errorMessage
```

Ví dụ:

```
{
    "status": "FAILED",
    "errorMessage": "Unsupported image format"
}
```

---

# 7. Kết quả kiểm thử

Sau khi hoàn thành kiểm thử, hệ thống đạt được kết quả:

| Thành phần                       | Kết quả    |
| -------------------------------- | ---------- |
| Upload ảnh vào S3 Input Bucket   | Thành công |
| S3 Trigger gọi Lambda            | Thành công |
| Lambda xử lý ảnh                 | Thành công |
| Ảnh tối ưu lưu vào Output Bucket | Thành công |
| Thumbnail được tạo               | Thành công |
| Metadata lưu vào DynamoDB        | Thành công |
| Log xử lý lưu trong CloudWatch   | Thành công |

Quy trình upload và tối ưu ảnh đã được kiểm tra thành công, chứng minh hệ thống có khả năng tự động xử lý ảnh ngay sau khi người dùng tải ảnh lên.
