---
title: "Tổng quan Workshop"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---

#### Đặt bài toán

Tại nhiều trường học và trung tâm đào tạo, việc theo dõi kết quả học tập của sinh viên vẫn được thực hiện thủ công qua các bảng tính (spreadsheet) và các hệ thống rời rạc. Khi quy mô lớp học tăng lên, giảng viên thường phát hiện ra các sinh viên gặp khó khăn quá trễ, và việc can thiệp hỗ trợ học tập thường diễn ra khi không còn mang lại hiệu quả.

**Hệ thống Cảnh báo sớm Kết quả Học tập của Sinh viên (Student Performance Early Warning System)** giải quyết vấn đề này bằng cách tập trung hóa dữ liệu sinh viên, tự động dự báo nguy cơ học tập bằng mô hình Machine Learning, trực quan hóa các góc nhìn (insights) trên một bảng điều khiển (dashboard) và gửi cảnh báo đối với các sinh viên có nguy cơ cao.

#### Những gì nhóm tôi sẽ xây dựng

Chúng ta sẽ xây dựng một Hệ thống Thông tin hoàn toàn serverless với luồng hoạt động end-to-end như sau:

```
Tập dữ liệu CSV
    ↓
Amazon S3 (raw-data / predict-input)
    ↓
AWS Lambda (ingest + batch predict)
    ↓
Amazon DynamoDB (student_records + prediction_results)
    ↓
Amazon API Gateway (REST)
    ↓
React Dashboard (S3 + CloudFront)

Amazon SageMaker Endpoint (XGBoost)  →  Xác suất rủi ro
Amazon SNS                            →  Cảnh báo qua email cho nguy cơ cao
Amazon CloudWatch                     →  Nhật ký (logs), chỉ số (metrics), cảnh báo (alarms)
```

#### Các dịch vụ AWS được sử dụng

| Tầng (Layer) | Dịch vụ AWS | Mục đích |
|-------|-------------|---------|
| Frontend | Amazon S3 + CloudFront | Lưu trữ và phân phối React dashboard |
| API | Amazon API Gateway | Cung cấp các điểm cuối REST (REST endpoints) |
| Compute | AWS Lambda | Xử lý logic nạp dữ liệu (ingestion), dự báo và CRUD |
| Database | Amazon DynamoDB | Hồ sơ sinh viên và kết quả dự báo |
| Storage | Amazon S3 | Tập dữ liệu và mô hình (artifacts) |
| Machine Learning | Amazon SageMaker | Phục vụ mô hình dự báo rủi ro đã được huấn luyện |
| Monitoring | Amazon CloudWatch | Logs, metrics và alarms |
| Notifications | Amazon SNS | Cảnh báo qua email cho các sinh viên có nguy cơ cao |
| Security | AWS IAM | Quản lý truy cập theo quyền tối thiểu (least-privilege) |


#### Tập dữ liệu (Dataset)

Workshop sử dụng tập dữ liệu gồm ~3.000 hồ sơ sinh viên chứa các đặc trưng về học tập và hành vi (chuyên cần, điểm bài tập và điểm thi, mức độ tham gia lớp học, nộp bài về nhà, số giờ học trực tuyến, hoạt động ngoại khóa và điểm tương tác hành vi) cùng với nhãn nhị phân `at_risk` được sử dụng làm mục tiêu dự báo.

![Dataset preview]( /fcj-workshop-template/images/5-Workshop/5.1-Workshop-overview/dataset-preview.png)

#### Vùng (Region)

Workshop này sử dụng vùng **Châu Á Thái Bình Dương (Singapore) `ap-southeast-1`**. Hãy đảm bảo mọi tài nguyên (S3, Lambda, DynamoDB, API Gateway, SageMaker) đều được tạo trong **cùng một region** để tránh các lỗi liên vùng.

{{% notice tip %}}
Hãy giữ tất cả tài nguyên trong cùng một region. Lỗi `ResourceNotFoundException` thường xảy ra do hàm Lambda ở region này cố gắng truy cập vào bảng DynamoDB ở một region khác.
{{% /notice %}}