---
title: "Model & SageMaker Endpoint"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 5.5.1. </b> "
---

#### Train and evaluate

The dataset already contains the `at_risk` label, so this is supervised binary classification. Train locally with scikit-learn (or use SageMaker training), evaluate, and record accuracy for the report [1].

```python
X = df[["attendance_rate", "assignment_avg_score", "exam_avg_score",
        "homework_submission_rate", "class_participation"]]
y = df["at_risk"]
```

Capture the accuracy and classification report screenshots as evidence of ML integration.

![Model accuracy]( /fcj-workshop-template/images/5-Workshop/5.5-ML/accuracy.png)

#### Deploy the SageMaker endpoint

Deploy the trained model as a **SageMaker endpoint** (XGBoost) that accepts CSV input and returns a probability per row.

{{% notice warning %}}
A SageMaker endpoint runs on a backing instance **24/7 and is billed continuously**, even when idle. 
{{% /notice %}}

Verify the endpoint status is **InService**.

![SageMaker endpoint]( /fcj-workshop-template/images/5-Workshop/5.5-ML/endpoint.png)