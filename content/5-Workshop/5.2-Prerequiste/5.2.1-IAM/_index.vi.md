---
title: "Thiết lập Tài khoản AWS & IAM"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 5.2.1. </b> "
---

#### Tạo người dùng IAM (IAM user)

Không sử dụng tài khoản Root cho các hoạt động phát triển hàng ngày. Hãy tạo một người dùng IAM riêng biệt và bật MFA, tuân thủ Nguyên tắc Quyền tối thiểu (Principle of Least Privilege).

1. Truy cập **IAM → Users → Create user**.
2. Tên người dùng (User name): `student-warning-dev`.
3. Bật tùy chọn **Provide user access to the AWS Management Console**.
4. Gán các chính sách (policies) cần thiết cho workshop này:
   - `AmazonS3FullAccess`
   - `AmazonDynamoDBFullAccess`
   - `AWSLambda_FullAccess`
   - `AmazonAPIGatewayAdministrator`
   - `CloudWatchFullAccess`
   - `AmazonSNSFullAccess`
   - `AmazonSageMakerFullAccess`

![IAM user creation]( /fcj-workshop-template/images/5-Workshop/5.2-Prerequisite/iam-user.png)

#### Bật MFA (Xác thực hai yếu tố)

Tại mục **Security credentials → Multi-factor authentication (MFA)**, hãy đăng ký một ứng dụng xác thực (Google Authenticator / Authy). Điều này giúp bảo mật việc đăng nhập console và nâng cao điểm Bảo mật (Security score) cho dự án.

![Enable MFA]( /fcj-workshop-template/images/5-Workshop/5.2-Prerequisite/mfa.png)

#### Tạo Access Key cho CLI

Tại mục **Security credentials → Create access key → Command Line Interface (CLI)**, hãy tạo một Access Key ID và Secret Access Key.

{{% notice warning %}}
Secret Access Key chỉ hiển thị **duy nhất một lần**. Hãy lưu trữ nó an toàn và không bao giờ commit lên Git hoặc viết trực tiếp (hard-code) vào mã nguồn của bạn.
{{% /notice %}}

#### Vai trò thực thi cho Lambda (Lambda execution role)

Các hàm Lambda không được sử dụng thông tin đăng nhập viết cứng (hard-coded). Chúng ủy quyền thông qua một **execution role**. Hãy tạo role này ngay bây giờ:

1. **IAM → Roles → Create role**.
2. Loại thực thể tin cậy (Trusted entity type): **AWS service**.
3. Trường hợp sử dụng (Use case): **Lambda**.
4. Gán các policy:
   - `AWSLambdaBasicExecutionRole` (CloudWatch Logs)
   - `AmazonS3ReadOnlyAccess`
   - `AmazonDynamoDBFullAccess`
5. Tên Role (Role name): `StudentWarningLambdaRole`.

{{% notice info %}}
Role **bắt buộc** phải tin cậy `lambda.amazonaws.com`. Nếu bạn tạo role cho một dịch vụ khác, nó sẽ không xuất hiện trong danh sách thả xuống "existing role" của Lambda.
{{% /notice %}}

![Lambda role trust relationship]( /fcj-workshop-template/images/5-Workshop/5.2-Prerequisite/lambda-role.png)