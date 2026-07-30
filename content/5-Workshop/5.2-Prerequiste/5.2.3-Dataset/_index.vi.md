---
title: "Chuẩn bị Tập dữ liệu"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 5.2.3. </b> "
---

#### Cấu trúc tập dữ liệu (Dataset schema)

Tập dữ liệu (`student_performance.csv`) chứa ~3.000 dòng. Mô hình sử dụng 5 đặc trưng số cốt lõi sau, theo đúng thứ tự chính xác này:

```text
attendance_rate
assignment_avg_score
exam_avg_score
homework_submission_rate
class_participation
```

Cột mục tiêu (target column) là `at_risk` (0 = không có nguy cơ, 1 = có nguy cơ).


#### Cấu trúc dự án cục bộ (tham khảo)

```text
student-warning-system/
├── backend/
│   ├── lambda/
│   │   ├── get_students/
│   │   ├── upload_dataset/
│   │   ├── predict_risk/          # dự báo theo đợt (batch predict)
│   │   ├── predict_ondemand/      # POST /predict
│   │   ├── create_student/
│   │   ├── update_student/
│   │   └── delete_student/
│   └── model/
│       ├── EDA.ipynb
├── frontend/
├── dataset/raw/student_performance.csv
└── requirements.txt
```

![Dataset in S3]( /images/5-Workshop/5.2-Prerequisite/dataset-s3.png)