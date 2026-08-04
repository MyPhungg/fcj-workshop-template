---
title: "Dọn dẹp tài nguyên AWS sau triển khai"
date: 2026-08-04
weight: 7
chapter: false
pre: " <b> 5.7 </b> "
---

# Dọn dẹp tài nguyên AWS sau triển khai

Sau khi hoàn thành quá trình triển khai hệ thống **Automatic Image Optimization System on AWS**, cần thực hiện dọn dẹp các tài nguyên AWS không còn sử dụng để tránh phát sinh chi phí ngoài mong muốn.

Việc cleanup giúp:

- Xóa các tài nguyên thử nghiệm.
- Giảm chi phí vận hành AWS.
- Tránh việc để lại các dịch vụ chạy nền không cần thiết.
- Đảm bảo tài khoản AWS luôn được quản lý hiệu quả.

---

# Các tài nguyên cần kiểm tra trước khi xóa

Trong hệ thống này, các tài nguyên AWS đã được triển khai gồm:

```
AWS Resources

├── Amazon S3
│   ├── Input Bucket
│   └── Output Bucket
│
├── AWS Lambda
│   └── image-optimizer-lambda
│
├── Amazon DynamoDB
│   └── ImageMetadata
│
├── Amazon CloudWatch
│   └── Lambda Logs
│
├── Amazon SNS
│   └── Notification Topic
│
└── IAM
    └── Lambda Execution Role
```

---

# 1. Xóa dữ liệu trong S3 Bucket

Trước khi xóa S3 Bucket, cần xóa toàn bộ object bên trong.

Các bucket cần kiểm tra:

```
auto-images-input-bucket

auto-images-output-bucket
```

Thực hiện:

1. Truy cập Amazon S3 Console.
2. Chọn Bucket cần xóa.
3. Chọn toàn bộ object.
4. Chọn:

```
Delete
```

5. Xác nhận xóa dữ liệu.

{{% notice warning %}}
Cần kiểm tra dữ liệu trước khi xóa vì thao tác xóa object trong S3 có thể không khôi phục được.
{{% /notice %}}

---

# 2. Xóa S3 Bucket

Sau khi đã xóa toàn bộ dữ liệu:

Chọn:

```
Delete bucket
```

Nhập tên bucket để xác nhận.

Ví dụ:

```
auto-images-input-bucket

auto-images-output-bucket
```

---

# 3. Xóa AWS Lambda Function

Truy cập:

```
AWS Lambda Console
```

Chọn:

```
image-optimizer-lambda
```

Chọn:

```
Actions
    |
    Delete function
```

Lambda Function sẽ bị xóa khỏi hệ thống.

---

# 4. Xóa DynamoDB Table

Truy cập:

```
Amazon DynamoDB
```

Chọn Table:

```
ImageMetadata
```

Chọn:

```
Delete table
```

Xác nhận:

```
Delete
```

Sau khi xóa, toàn bộ metadata lưu trữ trong bảng sẽ bị loại bỏ.

---

# 5. Xóa CloudWatch Logs

CloudWatch Logs có thể tiếp tục lưu trữ sau khi Lambda bị xóa.

Truy cập:

```
Amazon CloudWatch
```

Chọn:

```
Logs
    |
    Log groups
```

Xóa log group:

```
/aws/lambda/image-optimizer-lambda
```

---

# 6. Xóa SNS Topic

Truy cập:

```
Amazon SNS
```

Chọn Topic:

```
image-processing-alerts
```

Chọn:

```
Delete topic
```

SNS Subscription cũng sẽ được xóa theo Topic.

---

# 7. Kiểm tra IAM Role

Sau khi xóa Lambda, kiểm tra IAM Role:

```
image-optimizer-lambda-role
```

Nếu không còn Lambda nào sử dụng:

Có thể xóa Role để tránh dư thừa quyền truy cập.

{{% notice note %}}
Không nên xóa IAM Role nếu tài khoản vẫn còn sử dụng cho các Lambda Function hoặc dịch vụ khác.
{{% /notice %}}

---

# 8. Kiểm tra Billing

Sau khi cleanup, kiểm tra chi phí AWS:

Truy cập:

```
AWS Billing Console
```

Kiểm tra:

- S3 Storage.
- Lambda Requests.
- DynamoDB Usage.
- CloudWatch Logs.
- SNS Requests.

Đảm bảo không còn tài nguyên phát sinh chi phí.

---

# Kết quả

Sau khi hoàn thành cleanup:

- Các tài nguyên thử nghiệm được xóa.
- Không còn dịch vụ AWS chạy ngoài mục đích sử dụng.
- Giảm nguy cơ phát sinh chi phí không mong muốn.

Quy trình triển khai hoàn chỉnh:

```
5.3 S3 Deployment
        |
        v
5.4 Lambda Deployment
        |
        v
5.5 DynamoDB Deployment
        |
        v
5.6 Monitoring
        |
        v
5.7 Clean Up
```

Hệ thống **Automatic Image Optimization System on AWS** đã hoàn thành toàn bộ quá trình triển khai, kiểm thử và quản lý tài nguyên AWS.
