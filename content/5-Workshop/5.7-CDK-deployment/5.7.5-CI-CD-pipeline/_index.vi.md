---
title: "Tự động hóa CI/CD với GitHub Actions"
date: 2026-08-07
weight: 5
chapter: false
pre: " <b> 5.7.5. </b> "
---

---

Sau khi hoàn thành quá trình triển khai thủ công, nhóm sử dụng **GitHub Actions** để tự động hóa quy trình **Continuous Integration và Continuous Deployment (CI/CD)**.

Workflow được định nghĩa trong file:

```text id="q5k2mz"
.github/workflows/deploy.yml
```

Khi có thay đổi mới được push lên nhánh `main`, GitHub Actions sẽ tự động thực hiện các bước cần thiết để cập nhật Backend và Frontend trên môi trường AWS.

### Bước 1: Cấu hình GitHub Secrets

Để GitHub Actions có thể truy cập và triển khai tài nguyên trên AWS, cần cấu hình các thông tin xác thực dưới dạng **GitHub Secrets**.

Truy cập repository của dự án trên GitHub, sau đó chọn:

**Settings → Secrets and variables → Actions**

Thêm các Secret sau:

| Secret                  | Mô tả                                                                             |
| ----------------------- | --------------------------------------------------------------------------------- |
| `AWS_ACCESS_KEY_ID`     | Access Key của IAM User được sử dụng để triển khai AWS                            |
| `AWS_SECRET_ACCESS_KEY` | Secret Access Key tương ứng                                                       |
| `AWS_SESSION_TOKEN`     | Session Token, sử dụng khi AWS credential là temporary credential như AWS Academy |
| `VITE_GOOGLE_CLIENT_ID` | Google OAuth Client ID được sử dụng cho chức năng đăng nhập bằng Google           |

> **Lưu ý:** `AWS_SESSION_TOKEN` chỉ cần thiết khi sử dụng temporary credentials. Với Access Key/Secret Key thông thường, Secret này có thể không cần cấu hình.

Các thông tin xác thực được lưu dưới dạng GitHub Secrets để tránh đưa trực tiếp credential vào source code.

---

### Bước 2: Kích hoạt CI/CD Pipeline

Workflow được cấu hình để chạy khi có code mới được push lên nhánh `main`.

Quy trình tổng quát:

```text id="5y0jrz"
Developer
    │
    │ git push
    ▼
GitHub Repository
    │
    ▼
GitHub Actions
    │
    ├──► Setup Python
    │
    ├──► Setup Node.js
    │
    ├──► Install AWS CDK
    │
    ├──► Deploy Backend
    │
    ├──► Get CDK Outputs
    │
    ├──► Build Frontend
    │
    └──► Deploy to AWS Amplify
```

Nhờ đó, developer không cần thực hiện thủ công toàn bộ các lệnh triển khai sau mỗi lần cập nhật source code.

---

### Bước 3: Triển khai Backend

Sau khi workflow được kích hoạt, GitHub Actions chuẩn bị môi trường cần thiết cho dự án, bao gồm Python, Node.js và AWS CDK.

Sau đó, workflow thực hiện triển khai các CDK Stack bằng lệnh:

```bash id="1s5a4d"
cdk deploy --all
```

Các thay đổi trong mã nguồn CDK sẽ được kiểm tra và cập nhật lên môi trường AWS.

Nếu Backend được triển khai thành công, các giá trị output của CDK sẽ được sử dụng cho các bước tiếp theo của pipeline.

---

### Bước 4: Lấy thông tin từ CDK Output

Sau khi Backend deployment hoàn tất, workflow truy xuất các giá trị cần thiết từ CDK output, chẳng hạn như:

- `ApiGatewayUrl`: Địa chỉ API Gateway được sử dụng bởi Frontend.
- `AmplifyAppId`: ID của ứng dụng AWS Amplify.

Các thông tin này giúp pipeline có thể cấu hình và triển khai Frontend theo đúng tài nguyên Backend vừa được cập nhật.

---

### Bước 5: Build Frontend

Sau khi lấy được API Gateway URL, workflow tiến hành build ứng dụng React/Vite.

Biến môi trường API được cấu hình để Frontend sử dụng API Gateway mới nhất:

```text id="3b6x2v"
VITE_API_GATEWAY_URL
```

Sau đó, ứng dụng được build thành các file tĩnh để chuẩn bị triển khai:

```bash id="8r4h2n"
npm install
npm run build
```

Kết quả build được tạo trong thư mục `dist`.

---

### Bước 6: Deploy Frontend lên AWS Amplify

Sau khi Frontend được build thành công, workflow đóng gói các file trong thư mục `dist` và thực hiện deployment lên **AWS Amplify**.

Quá trình này giúp phiên bản Frontend mới được cập nhật lên môi trường Live mà không cần thực hiện thủ công trên AWS Management Console.

Khi deployment hoàn tất, người dùng có thể truy cập phiên bản mới của ứng dụng thông qua URL được cung cấp bởi AWS Amplify.

---

### Kiểm tra CI/CD Pipeline

Sau khi push code lên nhánh `main`, có thể kiểm tra quá trình thực thi workflow bằng cách:

1. Truy cập repository trên GitHub.
2. Chọn tab **Actions**.
3. Chọn workflow triển khai.
4. Theo dõi trạng thái của từng bước.
5. Kiểm tra workflow hoàn tất với trạng thái thành công.

Nếu tất cả các bước đều hoàn thành thành công, Backend và Frontend đã được cập nhật lên môi trường AWS.

#### Kết quả

Sau khi CI/CD Pipeline được cấu hình, quy trình triển khai của hệ thống được tự động hóa theo luồng:

```text id="r5j0kg"
Push code lên main
        │
        ▼
GitHub Actions
        │
        ├──► Deploy AWS CDK
        │
        ├──► Lấy API Gateway URL
        │
        ├──► Build React Frontend
        │
        └──► Deploy AWS Amplify
```

Việc áp dụng CI/CD giúp giảm thiểu các thao tác triển khai thủ công, hạn chế sai sót trong quá trình cập nhật hệ thống và rút ngắn thời gian đưa phiên bản mới lên môi trường AWS.
