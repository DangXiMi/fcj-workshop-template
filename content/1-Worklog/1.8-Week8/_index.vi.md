---
title: "Week 8 Worklog"
date: 2026-07-20
weight: 8
chapter: false
build:
  list: always
  render: always
pre: " <b> 1.8. </b> "
---

### Mục tiêu Tuần 8:

* Tổng hợp tất cả kỹ năng đã học thành một dự án AI serverless từ đầu đến cuối.
* Xây dựng Hệ thống Cảnh báo Sớm Học sinh (Student Performance Early Warning System) hoàn chỉnh từ thu thập dữ liệu đến triển khai.
* Áp dụng kiến trúc serverless, Machine Learning và các dịch vụ AWS.
* Thực hiện thuyết trình và viết tài liệu cuối khóa.

### Nhiệm vụ thực hiện trong tuần (20 tháng 7 – 31 tháng 7):

| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | ---- | ---------- | --------------- | ------------------ |
| 1–2 | **Khởi động Dự án Cuối khóa:** <br>&emsp; + Xác định phạm vi và yêu cầu <br>&emsp; + Thiết kế sơ đồ kiến trúc (AWS Serverless) <br>&emsp; + Chọn nguồn dữ liệu và bài toán ML (XGBoost) | 20/07/2026 | 21/07/2026 | Project Guidelines |
| 3–4 | **Chuẩn bị dữ liệu & EDA:** <br>&emsp; + Làm sạch và biến đổi dữ liệu học sinh <br>&emsp; + Phân tích khám phá dữ liệu (EDA) <br>&emsp; + Lựa chọn và xây dựng đặc trưng | 22/07/2026 | 23/07/2026 | Training Notebook |
| 5–6 | **Phát triển và Huấn luyện Model:** <br>&emsp; + Huấn luyện XGBoost locally (scikit-learn) <br>&emsp; + Đánh giá model (độ chính xác 99.67%, AUC-ROC: 1.0) <br>&emsp; + Chuyển đổi sang định dạng XGBoost gốc cho SageMaker | 24/07/2026 | 25/07/2026 | SageMaker notebooks |
| 7–8 | **Triển khai Model & API Serverless:** <br>&emsp; + Deploy model lên SageMaker Serverless Endpoint <br>&emsp; + Xây dựng Lambda functions (CRUD + Dự đoán) <br>&emsp; + Tạo API Gateway REST API <br>&emsp; + Cấu hình S3 Trigger cho xử lý batch | 26/07/2026 | 27/07/2026 | MLOps workshops |
| 9–10 | **Tích hợp Ứng dụng & Frontend:** <br>&emsp; + Phát triển 7 Lambda functions (CRUD + Dự đoán) <br>&emsp; + Xây dựng React Dashboard (S3 + CloudFront) <br>&emsp; + Tích hợp cảnh báo email SNS cho học sinh có nguy cơ cao | 28/07/2026 | 29/07/2026 | Serverless workshops |
| 11–12 | **Kiểm thử, Giám sát & Tài liệu:** <br>&emsp; + Viết unit test và integration test <br>&emsp; + Thiết lập CloudWatch dashboard và 9 alarm <br>&emsp; + Chuẩn bị tài liệu và bài thuyết trình cuối khóa | 30/07/2026 | 31/07/2026 | Monitoring modules |

### Thành tựu đạt được Tuần 8:

#### Dự án Cuối khóa: "Hệ thống Cảnh báo Sớm Học sinh (SP-EWS)"

**Tổng quan kiến trúc:**
- **Frontend:** React Dashboard lưu trên S3 + CloudFront (CDN)
- **API:** Amazon API Gateway (REST API) – 6 endpoints
- **Compute:** AWS Lambda (7 functions – CRUD + Dự đoán)
- **ML Model:** XGBoost (độ chính xác 99.67%) triển khai trên SageMaker Serverless
- **Database:** Amazon DynamoDB (2 bảng: `student_records`, `prediction_results`)
- **Storage:** Amazon S3 (Frontend hosting, upload CSV, artifact model)
- **Batch Processing:** S3 Trigger → Lambda (predictRiskFunction) → SageMaker → SNS
- **Dự đoán theo thời gian thực:** Lambda (predictRiskOnDemand) → SageMaker → JSON Response
- **Thông báo:** Amazon SNS (Email cảnh báo học sinh có nguy cơ cao)
- **Giám sát:** Amazon CloudWatch (Logs, Metrics, 9 Alarms)
- **Bảo mật:** IAM Least Privilege

#### Các kết quả bàn giao chính:
* **Kho mã nguồn:** Tất cả Lambda functions, React frontend và notebook huấn luyện trên GitHub.
* **Hạ tầng AWS:** Triển khai đầy đủ hệ thống serverless với 9 dịch vụ AWS.
* **Live Demo:** React dashboard truy cập qua CloudFront URL.
* **Tài liệu:** Hướng dẫn hoàn chỉnh (10 phần), sơ đồ kiến trúc và hướng dẫn cài đặt.
* **Thuyết trình:** Trình bày 30 phút về các quyết định, thách thức và kết quả.
* **Blog Posts:** Chuỗi 3 bài viết (SageMaker Serverless, Batch Processing, SNS Alerts).

### Bài học kinh nghiệm chính:

> **Suy ngẫm cuối khóa:** Hành trình 8 tuần đã bao phủ toàn bộ bức tranh AI/ML trên AWS – từ các dịch vụ nền tảng đến MLOps nâng cao và tích hợp serverless. Tôi đã có trải nghiệm thực tế trong việc xây dựng các hệ thống AI sẵn sàng cho sản xuất, tuân thủ các best practice về bảo mật, khả năng mở rộng và bảo trì. Kỳ thực tập đã cung cấp nền tảng vững chắc cho sự nghiệp Kỹ sư AI trên nền tảng AWS.

> **Những bài học quan trọng:**
> 1. **Giới hạn Lambda Layer:** Việc đóng gói thư viện ML (`xgboost`, `joblib`, `numpy`) trong Lambda Layer vượt quá giới hạn 250 MB → chuyển sang SageMaker Serverless.
> 2. **Tính nhất quán của đặc trưng:** Các đặc trưng phải được gửi đến SageMaker đúng thứ tự và định dạng như khi huấn luyện (giá trị thô, không chuẩn hóa).
> 3. **Xử lý Batch:** Xử lý 3.000 học sinh yêu cầu `BATCH_SIZE=500` để tránh timeout Lambda.
> 4. **Xác nhận SNS:** Email subscription yêu cầu xác nhận thủ công (kiểm tra thư mục spam).
> 5. **Chi phí Serverless:** Tổng chi phí hàng tháng khoảng $0.05 – $0.10 (về 0 khi không sử dụng).
> 6. **Tích hợp End‑to‑End:** Dự đoán thời gian thực (API Gateway → Lambda → SageMaker) và dự đoán batch (S3 Trigger → Lambda → SageMaker → SNS) hoạt động cùng nhau.

### Các dịch vụ AWS đã sử dụng:

| Dịch vụ | Mục đích |
| :--- | :--- |
| **S3** | Lưu trữ frontend, upload CSV, artifact model |
| **CloudFront** | CDN cho React dashboard |
| **API Gateway** | REST API (6 endpoints) |
| **Lambda** | 7 hàm serverless (CRUD + Dự đoán) |
| **DynamoDB** | 2 bảng: `student_records`, `prediction_results` |
| **SageMaker** | Serverless XGBoost endpoint |
| **SNS** | Cảnh báo email cho học sinh nguy cơ cao |
| **CloudWatch** | Logs, metrics, 9 alarm |
| **IAM** | Bảo mật và phân quyền tối thiểu |