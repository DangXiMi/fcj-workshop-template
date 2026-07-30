---
title: "Mô hình & SageMaker Endpoint"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 5.5.1. </b> "
---

#### Huấn luyện và đánh giá mô hình

Tập dữ liệu đã bao gồm sẵn nhãn `at_risk`, do đó đây là bài toán phân loại nhị phân có giám sát (supervised binary classification). Huấn luyện mô hình cục bộ bằng scikit-learn (hoặc sử dụng dịch vụ huấn luyện của SageMaker), đánh giá và ghi lại độ chính xác (accuracy) để đưa vào báo cáo.

```python
X = df[["attendance_rate", "assignment_avg_score", "exam_avg_score",
        "homework_submission_rate", "class_participation"]]
y = df["at_risk"]
```

Chụp lại màn hình kết quả độ chính xác và báo cáo phân loại (classification report) để làm bằng chứng chứng minh việc tích hợp Machine Learning.

![Model accuracy]( /images/5-Workshop/5.5-ML/accuracy.png)

#### Triển khai SageMaker endpoint

Triển khai mô hình đã huấn luyện thành một **SageMaker endpoint** (XGBoost) nhận đầu vào định dạng CSV và trả về giá trị xác suất cho mỗi dòng dữ liệu.

{{% notice warning %}}
Một SageMaker endpoint chạy trên một hạ tầng máy chủ cơ sở **24/7 và tính phí liên tục**, ngay cả khi không có lưu lượng truy cập (rảnh rỗi).
{{% /notice %}}

Kiểm tra trạng thái của endpoint để đảm bảo đã chuyển sang trạng thái **InService**.

![SageMaker endpoint]( /images/5-Workshop/5.5-ML/endpoint.png)