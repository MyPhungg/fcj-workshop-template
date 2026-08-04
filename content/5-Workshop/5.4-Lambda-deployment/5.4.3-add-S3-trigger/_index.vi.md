---
title: "Cấu hình S3 Event Trigger cho AWS Lambda"
date: 2026-08-04
weight: 3
chapter: false
pre: " <b> 5.4.3 </b> "
---

# Cấu hình S3 Event Trigger cho AWS Lambda

Trong hệ thống **Automatic Image Optimization System on AWS**, Lambda Function được kích hoạt tự động khi người dùng tải ảnh mới lên Amazon S3 Input Bucket.

S3 Event Trigger giúp hệ thống thực hiện quy trình xử lý ảnh tự động:

```
User Upload Image
        |
        v
Input S3 Bucket
        |
        | Object Created Event
        v
AWS Lambda
        |
        +--> Optimize Image
        |
        +--> Generate Thumbnail
        |
        +--> Save Metadata
        |
        v
Output S3 Bucket
```

---

# 1. Truy cập Lambda Trigger Configuration

Mở AWS Lambda Console:

```
https://console.aws.amazon.com/lambda/
```

Chọn Lambda Function:

```
image-optimizer-lambda
```

Trong giao diện Lambda:

Chọn:

```
Function overview
```

Sau đó chọn:

```
Add trigger
```

để thêm nguồn kích hoạt cho Lambda.

![add-trigger](/images/5-Workshop/5.4-Lambda/add-trigger/add-trigger.png)

---

# 2. Chọn nguồn Trigger là Amazon S3

Trong danh sách Trigger:

Chọn:

```
S3
```

Amazon S3 được sử dụng để gửi thông báo khi có object mới được tạo trong bucket.

![select-s3-trigger](/images/5-Workshop/5.4-Lambda/add-trigger/select-s3-trigger.png)

---

# 3. Cấu hình S3 Bucket Trigger

Trong phần cấu hình S3 Trigger:

## Bucket

Chọn Input Bucket của hệ thống:

```
auto-images-input-bucket
```

Bucket này chứa các ảnh gốc do người dùng tải lên.

---

## Event type

Chọn:

```
All object create events
```

Event này được kích hoạt khi có object mới được tạo trong S3.

Bao gồm:

- Upload ảnh mới.
- Copy object.
- Upload multipart.

![s3-event](/images/5-Workshop/5.4-Lambda/add-trigger/event-type.png)

---

## Prefix

Cấu hình:

```
uploads/
```

Lambda chỉ xử lý các file nằm trong thư mục:

```
uploads/
```

Ví dụ:

```
uploads/user001/image01.jpg
```

Khi file được upload vào đường dẫn này, S3 sẽ gửi event đến Lambda.

---

## Suffix

Cấu hình:

```
.jpg
```

hoặc mở rộng:

```
.jpeg
.png
.webp
```

Mục đích:

Chỉ kích hoạt Lambda đối với các file hình ảnh hợp lệ.

Ví dụ:

```
uploads/user001/photo.jpg
```

sẽ được xử lý.

Trong khi:

```
uploads/user001/document.pdf
```

sẽ không kích hoạt Lambda.

---

# 4. Xác nhận quyền giữa S3 và Lambda

Khi tạo Trigger, AWS sẽ tự động thêm quyền cho phép Amazon S3 gọi Lambda Function.

Trong Lambda:

Truy cập:

```
Configuration
    |
    +--> Permissions
```

Kiểm tra Resource-based policy.

Policy sẽ chứa quyền:

```json
{
  "Effect": "Allow",
  "Principal": {
    "Service": "s3.amazonaws.com"
  },
  "Action": "lambda:InvokeFunction"
}
```

Quyền này cho phép S3 gửi event đến Lambda.

---

# 5. Tạo Trigger

Sau khi hoàn thành cấu hình:

Click:

```
Add
```

AWS Lambda sẽ tạo kết nối giữa:

```
Amazon S3
        |
        |
        v
image-optimizer-lambda
```

![trigger-created](/images/5-Workshop/5.4-Lambda/add-trigger/trigger-created.png)

---

# 6. Kiểm tra Trigger đã được tạo

Sau khi thêm thành công, tại phần:

```
Function overview
```

sẽ hiển thị:

```
Triggers

Amazon S3
    |
    +--> auto-images-input-bucket
```

![lambda-trigger-success](/images/5-Workshop/5.4-Lambda/add-trigger/lambda-trigger-success.png)

---

# 7. Kiểm tra cấu hình S3 Notification

Có thể kiểm tra thêm tại Amazon S3:

Mở:

```
S3 Console
```

Chọn:

```
auto-images-input-bucket
```

Vào:

```
Properties
    |
    +--> Event notifications
```

Kết quả:

```
Event type:
Object Created

Destination:
AWS Lambda

Function:
image-optimizer-lambda
```

---

# 8. Luồng xử lý sau khi cấu hình Trigger

Sau khi hoàn thành cấu hình, hệ thống hoạt động như sau:

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
        +--------+--------+
        |                 |
        v                 v
 Optimize Image     Generate Thumbnail
        |                 |
        +--------+--------+
                 |
                 v
       auto-images-output-bucket
                 |
                 v
          DynamoDB Metadata
```

---

# 9. Kết quả

Sau bước này, Lambda Function đã được kết nối với Amazon S3 Input Bucket.

Hệ thống có khả năng:

- Tự động phát hiện ảnh mới được upload.
- Kích hoạt Lambda Function xử lý ảnh.
- Tạo ảnh tối ưu và thumbnail.
- Lưu kết quả vào Output Bucket.
- Ghi thông tin xử lý vào DynamoDB.

Bước tiếp theo sẽ thực hiện kiểm tra toàn bộ pipeline bằng cách upload ảnh mẫu và theo dõi kết quả xử lý trong **5.4.4-test-processing**.
