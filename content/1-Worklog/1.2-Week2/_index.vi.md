---
title: "Week 2 Worklog"
date: 2026-06-08
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu Tuần 2:

* Làm chủ tự động hóa serverless với AWS Lambda.
* Xây dựng backend serverless cho các ứng dụng AI.
* Hiểu về kiến trúc hướng sự kiện (event‑driven architecture).
* Bắt đầu xây dựng dự án Book Store Serverless.

### Nhiệm vụ thực hiện trong tuần:

| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | ---- | ---------- | --------------- | ------------------ |
| 1 | **Serverless Automation với AWS Lambda:** <br>&emsp; + Môi trường runtime và ngôn ngữ hỗ trợ <br>&emsp; + Cấu hình function và phân bổ bộ nhớ <br>&emsp; + Các loại trigger và event source | 08/06/2026 | 08/06/2026 | Lambda Documentation |
| 2 | **Lambda nâng cao:** <br>&emsp; + Layers và custom runtime <br>&emsp; + Quản lý biến môi trường và secret <br>&emsp; + Tích hợp VPC và networking <br>&emsp; + Giám sát với CloudWatch | 09/06/2026 | 09/06/2026 | Lambda Best Practices |
| 3 | **Serverless Backend với Lambda, S3 và DynamoDB:** <br>&emsp; + Thiết kế kiến trúc REST API serverless <br>&emsp; + Tạo Lambda function cho các thao tác CRUD <br>&emsp; + Tích hợp với API Gateway | 10/06/2026 | 10/06/2026 | Book Store Series – Phần 1 |
| 4 | **Frontend Development cho Serverless API:** <br>&emsp; + Thiết lập dự án frontend (React/JavaScript) <br>&emsp; + Kết nối frontend với API Gateway endpoint <br>&emsp; + Triển khai CRUD trên frontend | 11/06/2026 | 11/06/2026 | Book Store Series – Phần 2 |
| 5 | **Tự động hóa triển khai với AWS SAM:** <br>&emsp; + Cấu trúc và cú pháp SAM template <br>&emsp; + Định nghĩa tài nguyên (Lambda, API Gateway, DynamoDB) <br>&emsp; + Triển khai và quản lý ứng dụng | 12/06/2026 | 12/06/2026 | AWS SAM Documentation |
| 6 | **Xác thực người dùng với Amazon Cognito:** <br>&emsp; + Cấu hình Cognito User Pool <br>&emsp; + Thiết lập xác thực với Amplify <br>&emsp; + Triển khai luồng đăng ký, đăng nhập và đăng xuất | 13/06/2026 | 13/06/2026 | Cognito Workshop |

### Thành tựu đạt được Tuần 2:

#### Chuyên sâu về AWS Lambda
* Tạo và triển khai nhiều Lambda function.
* Viết function bằng Python và Node.js.
* Cấu hình trigger từ S3, API Gateway và DynamoDB Streams.
* Tối ưu hiệu năng qua điều chỉnh dung lượng bộ nhớ.
* Quản lý dependency bằng Lambda Layers.

#### Phát triển Backend Serverless
* Thiết kế và triển khai CRUD API sử dụng:
  - **API Gateway:** REST API với resource và method.
  - **Lambda:** Xử lý logic nghiệp vụ.
  - **DynamoDB:** Cơ sở dữ liệu NoSQL.
* Xây dựng cơ chế xử lý lỗi và định dạng response chuẩn.
* Thêm validation và transform cho request.

#### AWS SAM (Serverless Application Model)
* Tạo SAM template với:
  - Phần Globals cho cấu hình dùng chung.
  - Định nghĩa resource bằng cú pháp CloudFormation.
  - Event source cho trigger Lambda.
* Triển khai ứng dụng bằng `sam build` và `sam deploy`.
* Kiểm thử local với `sam local start‑api`.

#### Xác thực người dùng
* Thiết lập Cognito User Pool với:
  - Thuộc tính tùy chỉnh (custom attributes).
  - Chính sách mật khẩu.
  - Tùy chọn MFA (Multi‑Factor Authentication).
* Tích hợp Cognito với Amplify cho luồng xác thực frontend.
* Triển khai các chức năng: sign‑up, sign‑in, reset password, logout.

### Bài học kinh nghiệm chính:

> **Điểm nhấn:** Kiến trúc serverless giúp ứng dụng AI tự động mở rộng và giảm tải vận hành hạ tầng. Sự kết hợp Lambda + API Gateway + DynamoDB tạo ra backend chi phí thấp, linh hoạt và có độ phục hồi cao cho các tính năng ML.