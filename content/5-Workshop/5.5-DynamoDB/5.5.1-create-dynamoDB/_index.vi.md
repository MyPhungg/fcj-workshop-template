---
title: "Tạo DynamoDB Table lưu trữ Metadata"
date: 2026-08-04
weight: 1
chapter: false
pre: " <b> 5.5.1 </b> "
---

# Tạo DynamoDB Table lưu trữ Metadata

Trong hệ thống **Automatic Image Optimization System on AWS**, Amazon DynamoDB được sử dụng để lưu trữ metadata của các hình ảnh sau khi được AWS Lambda xử lý.

DynamoDB giúp hệ thống lưu lại thông tin:

- Tên file ảnh.
- Thông tin bucket nguồn và bucket kết quả.
- Trạng thái xử lý.
- Kích thước ảnh trước và sau tối ưu.
- Thời gian xử lý.
- Đường dẫn ảnh đã tối ưu và thumbnail.

---

# 1. Truy cập Amazon DynamoDB Console

Mở:

```
AWS Management Console
```

Tìm kiếm dịch vụ:

```
DynamoDB
```

Trong thanh điều hướng bên trái, chọn:

```
Tables
```

Sau đó chọn:

```
Create table
```

để tạo bảng DynamoDB mới.

![dynamodb-console](/images/5-Workshop/5.5-DynamoDB/create-dynamodb/dynamodb-console.png)

---

# 2. Cấu hình thông tin Table

Trong giao diện:

```
Create table
```

Cấu hình thông tin:

## Table name

Nhập:

```
ImageMetadata
```

Đây là bảng dùng để lưu thông tin metadata của các ảnh trong hệ thống.

---

## Partition Key

Thiết lập:

```
batchId
```

Kiểu dữ liệu:

```
String
```

`batchId` dùng để nhóm các ảnh được upload trong cùng một lần xử lý.

Ví dụ:

```
batchId:
8f7c9e12-xxxx-xxxx
```

Một batch có thể chứa nhiều ảnh khác nhau.

---

## Sort Key

Bật:

```
Add sort key
```

Nhập:

```
processingId
```

Kiểu dữ liệu:

```
String
```

`processingId` dùng để xác định duy nhất từng ảnh trong một batch.

Ví dụ:

```
batchId:
batch-001

processingId:
image-001
```

Cấu trúc khóa:

```
ImageMetadata

PK:
batchId

SK:
processingId
```

![table-key](/images/5-Workshop/5.5-DynamoDB/create-dynamodb/table-key.png)

---

# 3. Cấu hình Table Settings

Trong phần:

```
Table settings
```

Chọn:

```
Customize settings
```

để kiểm tra các cấu hình nâng cao.

---

## Capacity mode

Chọn:

```
On-demand
```

Lý do:

- Không cần quản lý số lượng read/write capacity.
- Tự động mở rộng theo lượng request.
- Phù hợp với hệ thống có lượng upload không cố định.

---

## Encryption

Giữ cấu hình:

```
Encryption at rest
Enabled
```

DynamoDB tự động mã hóa dữ liệu khi lưu trữ nhằm bảo vệ metadata của hệ thống.

---

# 4. Tạo DynamoDB Table

Sau khi hoàn thành cấu hình:

Nhấn:

```
Create table
```

AWS sẽ tiến hành tạo bảng.

Quá trình tạo mất một khoảng thời gian ngắn.

![create-table](/images/5-Workshop/5.5-DynamoDB/create-dynamodb/create-table.png)

---

# 5. Kiểm tra Table đã tạo

Sau khi tạo thành công, DynamoDB hiển thị:

```
Table name:

ImageMetadata
```

Thông tin:

```
Partition key:
batchId (String)

Sort key:
processingId (String)

Status:
Active
```

![table-created](/images/5-Workshop/5.5-DynamoDB/create-dynamodb/table-created.png)

---

# 6. Kiểm tra cấu trúc Table

Chọn:

```
ImageMetadata
```

Vào:

```
General information
```

Kiểm tra:

```
Primary key:

batchId
processingId
```

Ví dụ dữ liệu sẽ có dạng:

```json
{
  "batchId": "batch-001",
  "processingId": "processing-001",
  "originalName": "image.jpg",
  "status": "SUCCESS"
}
```

---

# 7. Cấu hình quyền truy cập cho Lambda

Để Lambda có thể ghi metadata vào DynamoDB, IAM Role của Lambda cần có quyền:

```
dynamodb:PutItem
dynamodb:UpdateItem
dynamodb:GetItem
dynamodb:Query
```

Role sử dụng:

```
image-optimizer-lambda-role
```

Luồng truy cập:

```
AWS Lambda
      |
      |
IAM Role
      |
      |
DynamoDB ImageMetadata
```

---

# 8. Kết quả

Sau bước này, DynamoDB Table đã được tạo thành công.

Thông tin hệ thống:

```
Table:

ImageMetadata


Primary Key:

batchId


Sort Key:

processingId


Capacity Mode:

On-demand


Encryption:

Enabled
```

DynamoDB đã sẵn sàng nhận metadata được gửi từ AWS Lambda sau quá trình xử lý ảnh.

Luồng hoàn chỉnh:

```
Amazon S3
     |
     |
Image Upload
     |
     v
AWS Lambda
     |
     |
Process Image
     |
     v
DynamoDB
     |
     |
ImageMetadata
```

Bước tiếp theo sẽ kiểm tra dữ liệu metadata được Lambda ghi vào DynamoDB trong **5.5.2-verify-metadata**.
