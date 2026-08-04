---
title: "Cấu hình AWS Lambda Function"
date: 2026-08-04
weight: 2
chapter: false
pre: " <b> 5.4.2 </b> "
---

# Cấu hình AWS Lambda Function xử lý ảnh

Sau khi tạo Lambda Function, bước tiếp theo là cấu hình các thành phần cần thiết để Lambda có thể thực hiện quá trình tối ưu hóa ảnh trong hệ thống **Automatic Image Optimization System on AWS**.

Các cấu hình bao gồm:

- Upload source code xử lý ảnh.
- Cấu hình biến môi trường.
- Điều chỉnh tài nguyên thực thi.
- Cấp quyền truy cập đến các AWS Service cần thiết.

---

# 1. Upload source code cho Lambda

Truy cập vào Lambda Function:

```
image-optimizer-lambda
```

Trong tab:

```
Code
```

Chọn:

```
Upload from
    |
    +--> .zip file
```

Upload file source code chứa chương trình xử lý ảnh.

Cấu trúc source code:

```
lambda-function/
│
├── lambda_function.py
├── requirements.txt
└── package/
    └── Pillow libraries
```

Trong đó:

- `lambda_function.py`: chứa logic xử lý sự kiện từ Amazon S3.
- `Pillow`: thư viện dùng để đọc, resize và tối ưu hình ảnh.
- `boto3`: thư viện tương tác với các dịch vụ AWS.

![upload-code](/images/5-Workshop/5.4-Lambda/configure-lambda/upload-code.png)

---

# 2. Cấu hình Handler

Trong phần:

```
Runtime settings
```

Chọn:

```
Edit
```

Cấu hình Handler:

```
lambda_function.lambda_handler
```

Giải thích:

- `lambda_function`: tên file Python chứa source code.
- `lambda_handler`: tên function được AWS Lambda gọi khi có event xảy ra.

Ví dụ:

```python
def lambda_handler(event, context):
    # Process S3 event
```

![lambda-handler](/images/5-Workshop/5.4-Lambda/configure-lambda/handler.png)

---

# 3. Cấu hình Environment Variables

Lambda sử dụng Environment Variables để lưu các thông tin cấu hình thay vì ghi trực tiếp trong source code.

Truy cập:

```
Configuration
    |
    +--> Environment variables
```

Chọn:

```
Edit
```

Thêm các biến môi trường:

| Key            | Value                     |
| -------------- | ------------------------- |
| OUTPUT_BUCKET  | auto-images-output-bucket |
| METADATA_TABLE | ImageMetadata             |
| MAX_WIDTH      | 1024                      |
| JPEG_QUALITY   | 80                        |
| THUMB_SIZE     | 150                       |

Ví dụ:

```
OUTPUT_BUCKET=
auto-images-output-bucket

METADATA_TABLE=
ImageMetadata
```

Các biến này được Lambda sử dụng trong quá trình:

- Xác định bucket lưu ảnh đã tối ưu.
- Lưu metadata vào DynamoDB.
- Thiết lập kích thước ảnh.
- Cấu hình chất lượng nén.

![environment-variable](/images/5-Workshop/5.4-Lambda/configure-lambda/environment-variable.png)

{{% notice note %}}
Việc sử dụng Environment Variables giúp tách biệt cấu hình và source code, giúp dễ dàng thay đổi tài nguyên AWS mà không cần chỉnh sửa chương trình.
{{% /notice %}}

---

# 4. Cấu hình tài nguyên thực thi

Do quá trình xử lý ảnh yêu cầu tải ảnh từ S3, resize và tạo thumbnail, Lambda cần được cấu hình tài nguyên phù hợp.

Truy cập:

```
Configuration
    |
    +--> General configuration
```

Chọn:

```
Edit
```

Cấu hình:

## Memory

Thiết lập:

```
512 MB
```

Memory cao hơn giúp cải thiện hiệu suất xử lý ảnh bằng thư viện Pillow.

---

## Timeout

Thiết lập:

```
1 minute
```

Lambda có đủ thời gian để thực hiện:

- Download ảnh từ Input Bucket.
- Xử lý và tối ưu hình ảnh.
- Tạo thumbnail.
- Upload ảnh kết quả.
- Ghi metadata vào DynamoDB.

![lambda-resource](/images/5-Workshop/5.4-Lambda/configure-lambda/resource.png)

---

# 5. Cấu hình IAM Permission cho Lambda

Lambda cần quyền truy cập đến các AWS Service được sử dụng trong hệ thống.

Truy cập:

```
Configuration
    |
    +--> Permissions
```

Chọn Execution Role:

```
image-optimizer-lambda-role
```

IAM Role cần được cấp các quyền:

---

## Amazon S3

Các quyền cần thiết:

```
s3:GetObject
s3:PutObject
```

Mục đích:

- Đọc ảnh gốc từ Input Bucket.
- Upload ảnh đã tối ưu vào Output Bucket.

---

## Amazon DynamoDB

Các quyền:

```
dynamodb:PutItem
dynamodb:UpdateItem
```

Mục đích:

- Lưu thông tin xử lý ảnh.
- Cập nhật trạng thái xử lý.

---

## CloudWatch Logs

Quyền:

```
AWSLambdaBasicExecutionRole
```

Mục đích:

- Ghi log khi Lambda thực thi.
- Theo dõi lỗi trong quá trình xử lý.

{{% notice warning %}}
Trong môi trường thực tế, không nên sử dụng các policy Full Access. Hệ thống nên sử dụng IAM Policy giới hạn đúng các tài nguyên mà Lambda cần truy cập theo nguyên tắc Least Privilege.
{{% /notice %}}

---

# 6. Cấu hình mã hóa

Hệ thống sử dụng AWS KMS để bảo vệ dữ liệu.

Trong phần cấu hình Lambda:

```
Configuration
    |
    +--> Environment variables
```

Kiểm tra:

```
Encryption configuration
```

Các thông tin cấu hình quan trọng có thể được mã hóa bằng AWS KMS Key nhằm đảm bảo an toàn dữ liệu.

---

# 7. Lưu cấu hình Lambda

Sau khi hoàn tất các thay đổi:

Click:

```
Save
```

AWS Lambda sẽ cập nhật lại cấu hình mới cho function.

---

# 8. Kiểm tra cấu hình hoàn tất

Sau khi cấu hình thành công, Lambda Function có thông tin:

```
Function name:
image-optimizer-lambda

Runtime:
Python 3.12

Handler:
lambda_function.lambda_handler

Memory:
512 MB

Timeout:
1 minute

Environment:
Configured

Execution Role:
image-optimizer-lambda-role
```

---

# 9. Kết quả

Sau bước này, Lambda Function đã được chuẩn bị đầy đủ để thực hiện quá trình xử lý ảnh.

Kiến trúc hiện tại:

```
                Amazon S3
                    |
                    |
            S3 Event Trigger
                    |
                    v
        image-optimizer-lambda
                    |
        +-----------+-----------+
        |                       |
        v                       v
 Optimize Image          Generate Thumbnail
        |                       |
        +-----------+-----------+
                    |
                    v
          Output S3 Bucket
                    |
                    v
             DynamoDB Metadata
```

Lambda Function sẽ tiếp tục được kết nối với **S3 Event Trigger** trong bước tiếp theo.
