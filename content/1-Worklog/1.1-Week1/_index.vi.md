---
title: "Week 1 Worklog"
date: 2026-06-15
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Mục tiêu Tuần 1:

* Làm quen với các thành viên của First Cloud AI Journey và hiểu cấu trúc chương trình thực tập.
* Thiết lập môi trường AWS và nắm vững các dịch vụ AWS cơ bản.
* Bắt đầu lộ trình Machine Learning Essentials.
* Hiểu tổng quan về các dịch vụ AI/ML trên AWS.

### Nhiệm vụ thực hiện trong tuần:

| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | ---- | ---------- | --------------- | ------------------ |
| 1 | - Giới thiệu team và buổi onboarding <br> - Xem lại nội quy, quy chế đơn vị thực tập <br> - Truy cập tài liệu trên nền tảng Cloud Journey | 15/06/2026 | 15/06/2026 | [Cloud Journey Platform](https://cloudjourney.awsstudygroup.com/) |
| 2 | - Tạo tài khoản AWS Free Tier (nếu chưa có) <br> - Thiết lập AWS Budgets để quản lý chi phí <br> - Cấu hình IAM user và role theo nguyên tắc phân quyền tối thiểu | 16/06/2026 | 16/06/2026 | AWS IAM Documentation |
| 3 | - **Machine Learning Essentials:** <br>&emsp; + Hiểu vòng đời ML (chuẩn bị dữ liệu → huấn luyện → đánh giá → triển khai) <br>&emsp; + Khám phá stack AI/ML của AWS (AI Services, ML Services, ML Frameworks) <br>&emsp; + Tìm hiểu khả năng và use case của SageMaker | 17/06/2026 | 17/06/2026 | ML Essentials Module |
| 4 | - **Amazon SageMaker Immersion Day – Phần 1:** <br>&emsp; + Thiết lập và làm quen SageMaker Studio <br>&emsp; + Tổng quan về các thuật toán built‑in <br>&emsp; + Gán nhãn dữ liệu với Ground Truth | 18/06/2026 | 18/06/2026 | SageMaker Documentation |
| 5 | - **Amazon SageMaker Immersion Day – Phần 2:** <br>&emsp; + Cấu hình và giám sát training job <br>&emsp; + Tối ưu siêu tham số (Hyperparameter Tuning) <br>&emsp; + Triển khai model lên endpoint | 19/06/2026 | 19/06/2026 | SageMaker Workshop |
| 6 | - **Data Lake Fundamentals on AWS:** <br>&emsp; + Hiểu kiến trúc Data Lake <br>&emsp; + S3 làm kho lưu trữ Data Lake <br>&emsp; + Glue Catalog và các ETL job | 20/06/2026 | 20/06/2026 | Data Lake Module |

### Thành tựu đạt được Tuần 1:

#### ✅ Nền tảng AWS
* Tạo và cấu hình thành công tài khoản AWS Free Tier kèm cảnh báo ngân sách.
* Thiết lập IAM user, group và policy theo các best practice về bảo mật.
* Nắm được hạ tầng toàn cầu của AWS (Region, Availability Zone, Edge Location).

#### ✅ Machine Learning Essentials
* Hiểu toàn bộ luồng công việc ML trên AWS từ đầu đến cuối.
* Khám phá stack AI/ML của AWS:
  * **AI Services** (các model đã được huấn luyện sẵn): Rekognition, Comprehend, Polly, Translate.
  * **ML Services** (nền tảng): SageMaker, Forecast, Personalize.
  * **ML Frameworks** (công cụ): TensorFlow, PyTorch, MXNet, scikit‑learn.

#### ✅ Amazon SageMaker cơ bản
* **SageMaker Studio:** Khởi chạy và cấu hình môi trường phát triển tích hợp.
* **Built‑in Algorithms:** Tìm hiểu các thuật toán có sẵn: Linear Learner, XGBoost, K‑Means, Deep Learning (Computer Vision, NLP).
* **Gán nhãn dữ liệu:** Tạo labeling job với Ground Truth (thủ công và tự động).
* **Huấn luyện:** Cấu hình và giám sát training job.
* **Tối ưu siêu tham số:** Tạo tuning job với các dải giá trị chỉ định.
* **Triển khai model:** Deploy thành công model đã huấn luyện lên real‑time endpoint.

#### ✅ Khái niệm Data Lake
* Nắm được nguyên lý kiến trúc Data Lake.
* Tạo S3 bucket với chính sách vòng đời phù hợp.
* Tìm hiểu AWS Glue Crawler và Data Catalog.

### Bài học kinh nghiệm chính:

> **Điểm nhấn:** AWS SageMaker cung cấp một nền tảng fully managed để xây dựng, huấn luyện và triển khai model ML ở quy mô lớn. Sự tích hợp giữa chuẩn bị dữ liệu (Glue), huấn luyện (SageMaker) và triển khai tạo nên một pipeline ML hoàn chỉnh, từ đầu đến cuối.