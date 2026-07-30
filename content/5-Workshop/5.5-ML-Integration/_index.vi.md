---
title: "Tích hợp Machine Learning"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5.5. </b> "
---

Tích hợp mô hình dự báo rủi ro: triển khai SageMaker endpoint, chạy dự báo theo đợt (batch prediction) trên tập dữ liệu, cung cấp API dự báo theo yêu cầu (on-demand), thêm các tính năng CRUD và gửi cảnh báo khi có nguy cơ cao.

```
Đặc trưng (Features) → SageMaker Endpoint (XGBoost) → Xác suất rủi ro
Dự báo đợt (Batch)   → prediction_results (DynamoDB) + Cảnh báo SNS
Theo yêu cầu         → POST /predict
```

#### Nội dung

1. [Mô hình & SageMaker Endpoint](5.5.1-Model-Endpoint/)
2. [Hàm Lambda Dự Báo Theo Đợt](5.5.2-Batch-Predict/)
3. [Dự Báo Theo Yêu Cầu & Các API CRUD](5.5.3-Predict-CRUD/)
4. [Tích Hợp Kết Quả Dự Báo Vào Dashboard](5.5.4-Dashboard-Integration/)