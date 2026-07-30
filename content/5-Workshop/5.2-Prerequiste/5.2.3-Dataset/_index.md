---
title: "Dataset Preparation"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 5.2.3. </b> "
---

#### Dataset schema

The dataset (`student_performance.csv`) contains ~3,000 rows. The model uses these five core numeric features, in this exact order:

```text
attendance_rate
assignment_avg_score
exam_avg_score
homework_submission_rate
class_participation
```

The target column is `at_risk` (0 = not at risk, 1 = at risk).


#### Local project structure (reference)

```text
student-warning-system/
├── backend/
│   ├── lambda/
│   │   ├── get_students/
│   │   ├── upload_dataset/
│   │   ├── predict_risk/          # batch predict
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