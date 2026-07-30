---
title: "Nhật ký tuần 8"
date: 2026-08-03
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
build:
  list: always
  render: always
---

### Mục tiêu Tuần 8:

* Tổng hợp tất cả kỹ năng đã học vào một dự án AI hoàn chỉnh.
* Xây dựng ứng dụng AI từ khâu thu thập dữ liệu đến triển khai.
* Áp dụng MLOps, serverless và các AI Services.
* Thuyết trình và hoàn thiện tài liệu cuối khóa.

### Nhiệm vụ thực hiện trong tuần (03/08 – 14/08):

| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | ---- | ---------- | --------------- | ------------------ |
| 1–2 | **Khởi động Dự án cuối khóa:** <br>&emsp; + Xác định phạm vi và yêu cầu <br>&emsp; + Thiết kế sơ đồ kiến trúc <br>&emsp; + Chọn nguồn dữ liệu và bài toán ML | 03/08/2026 | 04/08/2026 | Hướng dẫn đồ án |
| 3–4 | **Chuẩn bị dữ liệu và Feature Engineering:** <br>&emsp; + Sử dụng Glue và Athena làm sạch, biến đổi dữ liệu <br>&emsp; + Tạo feature group trong SageMaker Feature Store | 05/08/2026 | 06/08/2026 | Các workshop trước |
| 5–6 | **Phát triển và Huấn luyện model:** <br>&emsp; + Huấn luyện nhiều model (built‑in hoặc custom) <br>&emsp; + Thực hiện Hyperparameter Tuning <br>&emsp; + Đánh giá và chọn model tốt nhất | 07/08/2026 | 08/08/2026 | SageMaker notebooks |
| 7–8 | **Thiết lập MLOps Pipeline:** <br>&emsp; + Xây dựng SageMaker Pipeline để tự động retraining <br>&emsp; + Thiết lập CI/CD với CodePipeline và CDK <br>&emsp; + Triển khai Model Registry và phê duyệt | 09/08/2026 | 10/08/2026 | Các workshop MLOps |
| 9–10 | **Tích hợp ứng dụng và Frontend:** <br>&emsp; + Phát triển API serverless (Lambda + API Gateway) <br>&emsp; + Xây dựng frontend với React/Amplify <br>&emsp; + Tích hợp xác thực (Cognito) và AI Services | 11/08/2026 | 12/08/2026 | Các workshop serverless |
| 11–12 | **Kiểm thử, Giám sát & Tài liệu:** <br>&emsp; + Viết unit test và integration test <br>&emsp; + Thiết lập CloudWatch dashboard và alarm <br>&emsp; + Chuẩn bị tài liệu và thuyết trình cuối khóa | 13/08/2026 | 14/08/2026 | Các module giám sát |

### Thành tựu đạt được Tuần 8:

#### ✅ Dự án cuối khóa: "Hệ thống xử lý tài liệu thông minh"

**Tổng quan kiến trúc:**
- **Data Lake:** S3 cho dữ liệu thô và dữ liệu đã qua xử lý.
- **ETL:** AWS Glue (PySpark) để biến đổi dữ liệu.
- **Feature Store:** SageMaker Feature Store để tái sử dụng feature.
- **Huấn luyện:** SageMaker (XGBoost/Linear Learner) + Hyperparameter Tuning.
- **MLOps:** SageMaker Pipelines + Model Registry + CI/CD (CodePipeline).
- **Suy luận (Inference):** Real‑time endpoint cho dự đoán tức thời; batch inference qua Step Functions.
- **AI Services:** Comprehend cho trích xuất thực thể, Translate cho đa ngôn ngữ.
- **Frontend:** React với Amplify (Cognito auth, API Gateway).
- **Điều phối:** Step Functions cho workflow phức tạp.
- **Giám sát:** CloudWatch, X‑Ray cho tracing, và SageMaker Model Monitor.

#### Các sản phẩm chính của dự án:
* **Kho mã nguồn:** Toàn bộ Infrastructure as Code (CDK) và mã ứng dụng trên CodeCommit.
* **CI/CD Pipeline:** Tự động triển khai hạ tầng, model và ứng dụng.
* **Demo trực tiếp:** Ứng dụng web đầy đủ tính năng với AI tích hợp.
* **Tài liệu:** Sơ đồ kiến trúc, hướng dẫn cài đặt và hướng dẫn sử dụng.
* **Thuyết trình:** Trình bày 30 phút bao gồm các quyết định thiết kế, khó khăn gặp phải và kết quả đạt được.

### Bài học kinh nghiệm chính:

> **Suy ngẫm cuối khóa:** Hành trình 8 tuần đã bao phủ toàn bộ bức tranh AI/ML trên AWS – từ các dịch vụ nền tảng đến MLOps nâng cao và serverless. Tôi đã có trải nghiệm thực tế trong việc xây dựng các hệ thống AI sẵn sàng cho sản xuất, tuân thủ các best practice về bảo mật, khả năng mở rộng và bảo trì. Kỳ thực tập này đã cung cấp nền tảng vững chắc cho sự nghiệp của một Kỹ sư AI trên nền tảng AWS.