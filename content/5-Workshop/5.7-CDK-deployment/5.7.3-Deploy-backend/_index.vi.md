---
title: "Triển khai Backend bằng AWS CDK"
date: 2026-08-07
weight: 3
chapter: false
pre: " <b> 5.7.3. </b> "
---

---

Sau khi hoàn tất việc chuẩn bị môi trường, bước tiếp theo là triển khai hạ tầng Backend bằng **AWS CDK**.

Toàn bộ hạ tầng Backend được định nghĩa dưới dạng **IaC** và được tổ chức thành 5 CDK Stack:

- `StorageStack`: Triển khai các tài nguyên lưu trữ của hệ thống.
- `ProcessingStack`: Triển khai các thành phần phục vụ quá trình xử lý hình ảnh.
- `BackendStack`: Triển khai các thành phần Backend của ứng dụng.
- `ApiStack`: Triển khai API Gateway và cấu hình kết nối đến Backend.
- `AmplifyHostingStack`: Cấu hình tài nguyên phục vụ việc hosting Frontend trên AWS Amplify.

Các Stack được triển khai thông qua AWS CDK, giúp tự động tạo và cấu hình các tài nguyên AWS thay vì phải thực hiện thủ công trên AWS Management Console.

### Bước 1: Clone source code và tạo Virtual Environment

Clone source code của dự án từ repository:

```bash id="5p4d0w"
git clone https://github.com/MyPhungg/aws-automatic-image-optimization-system.git
```

Sau khi clone thành công, di chuyển vào thư mục dự án:

```bash id="m2yxde"
cd aws-automatic-image-optimization-system
```

Tạo Python Virtual Environment:

```bash id="6v8nqj"
python -m venv .venv
```

Kích hoạt Virtual Environment.

Trên **Windows**:

```bash id="qg1g7m"
.venv\Scripts\activate
```

Trên **Linux/macOS**:

```bash id="qz0jaf"
source .venv/bin/activate
```

Sau khi kích hoạt môi trường ảo, tiến hành cài đặt các thư viện cần thiết:

```bash id="a6rj4x"
pip install -r requirements.txt
```

Các thư viện này bao gồm những dependency cần thiết cho AWS CDK và các thành phần liên quan của dự án.

---

### Bước 2: Cấu hình Environment Variables

Một số thông tin cấu hình được sử dụng trong quá trình triển khai Backend. Tạo file `.env` tại thư mục:

```text id="2x2cwu"
backend/image-optimizer/.env
```

Nội dung mẫu:

```env id="86h2ol"
GOOGLE_CLIENT_ID=your-google-oauth-client-id
JWT_SECRET=your-secret-key-at-least-32-chars-long
```

Trong đó:

- `GOOGLE_CLIENT_ID`: Google OAuth Client ID được sử dụng cho chức năng đăng nhập bằng Google.
- `JWT_SECRET`: Secret key được sử dụng cho quá trình tạo và xác thực JWT.

Thay các giá trị mẫu bằng thông tin cấu hình thực tế của hệ thống.

> **Lưu ý:** File `.env` có thể chứa thông tin nhạy cảm. Không nên commit file này lên GitHub hoặc chia sẻ các giá trị secret thực tế.

---

### Bước 3: Bootstrap AWS CDK

Trước khi triển khai, AWS CDK cần được **bootstrap** trên AWS account và region sử dụng.

Nếu tài khoản AWS chưa được bootstrap, thực hiện:

```bash id="0f4j1x"
cdk bootstrap aws://<ACCOUNT_ID>/<REGION>
```

Trong đó:

- `<ACCOUNT_ID>` là AWS Account ID.
- `<REGION>` là AWS Region dùng để triển khai hệ thống.

Ví dụ:

```bash id="z8n7rc"
cdk bootstrap aws://123456789012/ap-southeast-1
```

Quá trình bootstrap tạo các tài nguyên cần thiết để AWS CDK có thể triển khai ứng dụng vào AWS environment.

> **Lưu ý:** Thông thường, mỗi AWS account và region chỉ cần bootstrap một lần. Nếu environment đã được bootstrap trước đó, có thể chuyển sang bước triển khai.

---

### Bước 4: Triển khai Backend Infrastructure

Sau khi hoàn tất bootstrap, thực hiện triển khai toàn bộ các CDK Stack bằng lệnh:

```bash id="75r1ba"
cdk deploy --all --require-approval never --outputs-file cdk-outputs.json
```

Trong đó:

- `--all`: Triển khai tất cả các CDK Stack trong project.
- `--require-approval never`: Không yêu cầu xác nhận thủ công đối với các thay đổi cần approval trong quá trình deploy.
- `--outputs-file cdk-outputs.json`: Lưu các giá trị output của các Stack vào file `cdk-outputs.json`.

AWS CDK sẽ đọc cấu hình từ source code, xác định các tài nguyên cần tạo hoặc cập nhật và thực hiện triển khai lên AWS.

Sau khi quá trình triển khai hoàn tất, file `cdk-outputs.json` sẽ chứa các thông tin được xuất ra từ các Stack. Các giá trị này có thể được sử dụng ở các bước triển khai Frontend và kiểm tra hệ thống.

---

### Bước 5: Build Docker Image cho Backend

Trong quá trình triển khai, một số Lambda của Backend được đóng gói dưới dạng **Docker Image** thông qua cấu hình `DockerImageFunction`.

AWS CDK sẽ sử dụng Docker trên máy local để build image tương ứng.

Quy trình tổng quát:

```text id="8fy2lv"
AWS CDK
   │
   ▼
Docker Build
   │
   ▼
Docker Image
   │
   ▼
Amazon ECR
   │
   ▼
AWS Lambda
```

Do đó, cần đảm bảo **Docker Desktop đang chạy** trước khi thực hiện lệnh `cdk deploy`.

Sau khi Docker image được build thành công, image sẽ được đưa vào **Amazon ECR** để Lambda sử dụng trong quá trình thực thi.

> **Lưu ý:** Quá trình build Docker image có thể mất thêm thời gian tùy thuộc vào kích thước source code, các dependency và tốc độ máy tính.
