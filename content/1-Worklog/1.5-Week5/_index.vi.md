---
title: "Week 5 Worklog"
date: 2026-06-29
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu Tuần 5:

* Đào sâu các tính năng nâng cao của Amazon SageMaker.
* Triển khai các thực hành MLOps: Feature Store, Pipelines, Model Registry.
* Khám phá giải thích model và phát hiện thiên lệch (bias) với Clarify.
* Tìm hiểu SageMaker Edge Manager và Neo.

### Nhiệm vụ thực hiện trong tuần:

| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | ---- | ---------- | --------------- | ------------------ |
| 1 | **SageMaker Feature Store:** <br>&emsp; + Tạo feature group <br>&emsp; + Nạp, truy xuất và chia sẻ feature <br>&emsp; + Online store so với Offline store | 29/06/2026 | 29/06/2026 | Feature Store Docs |
| 2 | **SageMaker Pipelines:** <br>&emsp; + Định nghĩa pipeline ML từ đầu đến cuối <br>&emsp; + Các bước: xử lý, huấn luyện, đánh giá, triển khai <br>&emsp; + Tự động hóa và điều phối pipeline | 30/06/2026 | 30/06/2026 | Pipelines Workshop |
| 3 | **Model Registry và Triển khai:** <br>&emsp; + Đăng ký model kèm metadata <br>&emsp; + Phê duyệt model để triển khai <br>&emsp; + Triển khai đa giai đoạn (staging, production) <br>&emsp; + Blue/green và canary deployment | 01/07/2026 | 01/07/2026 | Model Registry |
| 4 | **SageMaker Clarify:** <br>&emsp; + Phát hiện và đo lường thiên lệch (bias) <br>&emsp; + Giải thích model (SHAP) <br>&emsp; + Tạo báo cáo và giám sát | 02/07/2026 | 02/07/2026 | Clarify Docs |
| 5 | **SageMaker Edge Manager & Neo:** <br>&emsp; + Biên dịch model cho thiết bị biên (edge) <br>&emsp; + Triển khai lên edge với SageMaker Edge Manager <br>&emsp; + Giám sát model trên thiết bị biên | 03/07/2026 | 03/07/2026 | Edge Manager |
| 6 | **Thực hành: Xây dựng MLOps Pipeline hoàn chỉnh:** <br>&emsp; + Kết hợp Feature Store, Pipelines, Registry và Clarify <br>&emsp; + Tự động hóa retraining và triển khai | 04/07/2026 | 04/07/2026 | MLOps Workshop |

### Thành tựu đạt được Tuần 5:

#### SageMaker Feature Store
* Tạo feature group cho huấn luyện và suy luận.
* Nạp feature lịch sử và theo thời gian thực.
* Truy xuất feature cho model serving.
* Hiểu sự khác biệt giữa online store (low‑latency) và offline store (batch).

#### SageMaker Pipelines
* Xây dựng pipeline với các bước:
  - Tiền xử lý (Scikit‑learn / Spark).
  - Huấn luyện (built‑in hoặc custom algorithm).
  - Đánh giá (so sánh metric với baseline).
  - Bước điều kiện để đăng ký model nếu đạt ngưỡng.
* Lên lịch pipeline với EventBridge.
* Giám sát pipeline run qua SageMaker Studio.

#### Model Registry
* Đăng ký phiên bản model với metadata tùy chỉnh (độ chính xác, ngày, commit hash).
* Thiết lập trạng thái phê duyệt (pending, approved, rejected).
* Triển khai model đã được phê duyệt lên endpoint với alias khác nhau.

#### SageMaker Clarify
* Phân tích dữ liệu huấn luyện để phát hiện bias (trước huấn luyện).
* Phát hiện bias sau huấn luyện trên các nhóm được bảo vệ.
* Tạo giải thích SHAP để hiểu lý do dự đoán.
* Tạo báo cáo phục vụ cho yêu cầu tuân thủ (compliance).

#### Triển khai lên Edge
* Sử dụng SageMaker Neo để biên dịch model cho thiết bị biên (Raspberry Pi, Jetson Nano).
* Triển khai model đã biên dịch với SageMaker Edge Manager.
* Theo dõi trạng thái thiết bị và hiệu suất model trên toàn bộ fleet.

### Bài học kinh nghiệm chính:

> **Điểm nhấn:** MLOps là yếu tố quan trọng đối với ML ở môi trường sản xuất. SageMaker cung cấp bộ công cụ quản lý toàn bộ vòng đời: feature, pipeline, version model, giám sát và giải thích. Điều này giúp đảm bảo quy trình ML có thể tái lập, kiểm toán và mở rộng.