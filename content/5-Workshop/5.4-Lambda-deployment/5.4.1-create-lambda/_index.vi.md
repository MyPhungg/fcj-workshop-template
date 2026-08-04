---
title: "Tạo AWS Lambda Function"
date: 2026-08-04
weight: 1
chapter: false
pre: " <b> 5.4.1 </b> "
---

# Tạo AWS Lambda Function xử lý ảnh

Trong hệ thống **Automatic Image Optimization System on AWS**, AWS Lambda được sử dụng để thực hiện quá trình xử lý ảnh tự động sau khi người dùng tải ảnh lên Amazon S3.

Lambda function có nhiệm vụ:

- Nhận sự kiện từ Amazon S3.
- Đọc ảnh từ Input Bucket.
- Thực hiện tối ưu hóa ảnh bằng thư viện xử lý ảnh.
- Tạo ảnh thumbnail.
- Lưu ảnh kết quả vào Output Bucket.
- Ghi thông tin xử lý vào DynamoDB.

---

# 1. Truy cập AWS Lambda Console

Mở [AWS Lambda Console](https://console.aws.amazon.com/lambda/)

Trong thanh điều hướng bên trái, chọn:

```
Functions
```

Sau đó chọn:

```
Create function
```

để tạo Lambda Function mới.

![lambda-console](/images/5-Workshop/5.4-Lambda/create-lambda/lambda-console.png)

---

# 2. Chọn phương thức tạo Lambda Function

Trong giao diện **Create function**, chọn:

```
Author from scratch
```

Đây là phương thức tạo Lambda function từ source code được phát triển riêng cho hệ thống.

![author-from-scratch](/images/5-Workshop/5.4-Lambda/create-lambda/author-from-scratch.png)

---

# 3. Cấu hình thông tin Lambda Function

Trong phần **Basic information**, cấu hình:

## Function name

Nhập tên Lambda:

```
image-optimizer-lambda
```

Tên này được sử dụng để định danh function xử lý ảnh trong hệ thống.

---

## Runtime

Chọn runtime:

```
Python 3.12
```

Lambda sử dụng Python để xử lý ảnh với các thư viện:

- boto3: tương tác với các dịch vụ AWS.
- Pillow (PIL): xử lý và tối ưu hình ảnh.

![lambda-runtime](/images/5-Workshop/5.4-Lambda/create-lambda/runtime.png)

---

# 4. Cấu hình quyền thực thi cho Lambda

Trong phần **Change default execution role**:

Chọn:

```
Create a new role with basic Lambda permissions
```

AWS sẽ tự động tạo IAM Role để Lambda có quyền ghi log vào CloudWatch.

Ví dụ:

```
image-optimizer-lambda-role
```

Sau khi tạo Lambda, role này sẽ được bổ sung thêm quyền truy cập:

- Amazon S3.
- Amazon DynamoDB.
- AWS KMS (nếu sử dụng mã hóa).

{{% notice note %}}
Lambda cần IAM Role để có thể truy cập các AWS Service khác trong quá trình xử lý ảnh. Việc cấp quyền được thực hiện theo nguyên tắc Least Privilege, chỉ cấp những quyền cần thiết.
{{% /notice %}}

---

# 5. Cấu hình nâng cao

Trong phần **Advanced settings**, giữ cấu hình mặc định:

```
Enable function URL: Disabled
```

Hệ thống không sử dụng Lambda Function URL vì Lambda được kích hoạt thông qua S3 Event Trigger.

---

# 6. Tạo Lambda Function

Sau khi hoàn thành cấu hình:

Click:

```
Create function
```

AWS sẽ tạo Lambda function mới.

![create-function-success](/images/5-Workshop/5.4-Lambda/create-lambda/create-success.png)

---

# 7. Kiểm tra Lambda Function

Sau khi tạo thành công, giao diện Lambda sẽ hiển thị:

```
Function name:

image-optimizer-lambda
```

Các thông tin quan trọng:

```
Runtime:
Python 3.12

Architecture:
x86_64

Execution role:
image-optimizer-lambda-role
```

![lambda-created](/images/5-Workshop/5.4-Lambda/create-lambda/lambda-created.png)

---

# 8. Kết quả

Sau bước này, hệ thống đã có Lambda Function để thực hiện xử lý ảnh.

Cấu trúc triển khai:

```
Amazon S3
    |
    | Object Created Event
    |
    v
image-optimizer-lambda
    |
    +--> Optimize Image
    |
    +--> Generate Thumbnail
    |
    +--> Upload Result To S3
    |
    +--> Save Metadata To DynamoDB
```

Lambda Function sẽ tiếp tục được cấu hình source code, biến môi trường và quyền truy cập AWS Resource trong bước tiếp theo.
