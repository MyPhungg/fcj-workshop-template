---
title: "Cấu hình SNS Notification gửi cảnh báo"
date: 2026-08-04
weight: 2
chapter: false
pre: " <b> 5.6.2 </b> "
---

# Cấu hình SNS Notification gửi cảnh báo

Trong hệ thống **Automatic Image Optimization System on AWS**, Amazon SNS được sử dụng để gửi thông báo cảnh báo đến quản trị viên khi quá trình xử lý ảnh xảy ra lỗi.

SNS giúp hệ thống có khả năng thông báo tự động thay vì yêu cầu quản trị viên phải liên tục kiểm tra log trên CloudWatch.

Các trường hợp cần gửi cảnh báo:

- AWS Lambda xử lý ảnh thất bại.
- Không thể đọc ảnh từ S3.
- Không thể ghi metadata vào DynamoDB.
- Xảy ra lỗi trong quá trình tối ưu hóa ảnh.

---

# 1. Tổng quan luồng gửi Notification

Luồng hoạt động của SNS:

```
AWS Lambda
      |
      |
CloudWatch Logs
      |
      |
CloudWatch Alarm
      |
      |
Amazon SNS Topic
      |
      |
Email Notification
      |
      |
Administrator
```

Khi hệ thống phát hiện lỗi:

1. Lambda ghi nhận lỗi trong quá trình xử lý.
2. CloudWatch theo dõi trạng thái thực thi.
3. SNS gửi cảnh báo đến quản trị viên.

---

# 2. Truy cập Amazon SNS Console

Mở:

```
AWS Management Console
```

Tìm kiếm dịch vụ:

```
Simple Notification Service (SNS)
```

Trong thanh điều hướng bên trái chọn:

```
Topics
```

Sau đó chọn:

```
Create topic
```

để tạo SNS Topic mới.

![sns-console](/images/5-Workshop/5.6-Monitoring/sns-notification/sns-console.png)

---

# 3. Tạo SNS Topic

Trong giao diện:

```
Create topic
```

Chọn loại:

```
Standard
```

Cấu hình:

## Name

Nhập:

```
image-processing-alerts
```

Topic này được sử dụng để quản lý các thông báo cảnh báo của hệ thống.

---

## Display name

Nhập:

```
Image Processing Alert
```

Giúp dễ dàng nhận biết mục đích của Topic.

![create-topic](/images/5-Workshop/5.6-Monitoring/sns-notification/create-topic.png)

---

# 4. Tạo Subscription nhận thông báo

Sau khi tạo Topic, chọn:

```
Create subscription
```

Cấu hình:

## Protocol

Chọn:

```
Email
```

---

## Endpoint

Nhập email của quản trị viên nhận cảnh báo.

Ví dụ:

```
admin@example.com
```

Sau đó chọn:

```
Create subscription
```

![create-subscription](/images/5-Workshop/5.6-Monitoring/sns-notification/create-subscription.png)

---

# 5. Xác nhận Email Subscription

AWS SNS sẽ gửi email xác nhận đến địa chỉ đã đăng ký.

Mở email và chọn:

```
Confirm subscription
```

Sau khi xác nhận, trạng thái Subscription sẽ chuyển thành:

```
Confirmed
```

![confirm-subscription](/images/5-Workshop/5.6-Monitoring/sns-notification/confirm-subscription.png)

---

# 6. Kiểm tra SNS Topic

Sau khi cấu hình hoàn tất, SNS Topic hiển thị:

```
Topic name:

image-processing-alerts
```

Subscription:

```
Protocol:

Email


Status:

Confirmed
```

![topic-created](/images/5-Workshop/5.6-Monitoring/sns-notification/topic-created.png)

---

# 7. Cấu hình gửi cảnh báo từ CloudWatch

Để SNS nhận được cảnh báo, tạo CloudWatch Alarm dựa trên trạng thái Lambda.

Ví dụ điều kiện:

```
Metric:

Lambda Errors


Condition:

Errors >= 1
```

Khi Lambda xảy ra lỗi:

```
Lambda Error
      |
      |
CloudWatch Alarm
      |
      |
SNS Topic
      |
      |
Administrator Email
```

---

# 8. Kiểm tra gửi Notification

Thực hiện kiểm tra bằng cách tạo một lỗi trong quá trình xử lý ảnh.

Ví dụ:

- Upload file ảnh không được hỗ trợ.
- Lambda không có quyền truy cập S3.

Sau khi lỗi xảy ra:

CloudWatch ghi nhận:

```
ERROR

Image processing failed
```

SNS gửi email:

```
Subject:

AWS Notification


Message:

Image processing failed.

Function:
image-optimizer-lambda

Status:
FAILED
```

---

# 9. Kết quả

Sau khi hoàn thành cấu hình Amazon SNS, hệ thống có khả năng gửi cảnh báo tự động khi xảy ra lỗi.

Kết quả đạt được:

- SNS Topic được tạo thành công.
- Email quản trị viên được đăng ký nhận thông báo.
- Có thể kết nối với CloudWatch để gửi cảnh báo.
- Hỗ trợ phát hiện và xử lý sự cố nhanh chóng.

Luồng Monitoring hoàn chỉnh:

```
                AWS Lambda
                     |
                     |
              Image Processing
                     |
          +----------+----------+
          |                     |
          v                     v
   CloudWatch Logs        DynamoDB
          |
          |
   CloudWatch Alarm
          |
          |
          v
     Amazon SNS
          |
          |
          v
    Administrator
```

Sau bước này, hệ thống **Automatic Image Optimization System on AWS** đã hoàn thiện khả năng giám sát và gửi cảnh báo tự động trong quá trình xử lý ảnh.
