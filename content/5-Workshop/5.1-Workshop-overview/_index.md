---
title: "Workshop Overview"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---

#### Problem statement

In many schools and training centers, student performance is tracked manually across spreadsheets and disconnected systems. As class sizes grow, lecturers detect struggling students too late, and academic intervention often happens after it is no longer effective.

The **Student Performance Early Warning System** solves this by centralizing student data, automatically predicting academic risk with a Machine Learning model, visualizing insights on a dashboard, and sending alerts for high-risk students.

#### What we will build

We will build a fully serverless Information System with the following end-to-end flow:

```
CSV Dataset
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

Amazon SageMaker Endpoint (XGBoost)  →  Risk probability
Amazon SNS                            →  High-risk email alerts
Amazon CloudWatch                     →  Logs, metrics, alarms
```

#### AWS services used

| Layer | AWS Service | Purpose |
|-------|-------------|---------|
| Frontend | Amazon S3 + CloudFront | Host and deliver the React dashboard |
| API | Amazon API Gateway | Expose REST endpoints |
| Compute | AWS Lambda | Ingestion, prediction, and CRUD logic |
| Database | Amazon DynamoDB | Student records and prediction results |
| Storage | Amazon S3 | Datasets and model artifacts |
| Machine Learning | Amazon SageMaker | Serve the trained risk-prediction model |
| Monitoring | Amazon CloudWatch | Logs, metrics, and alarms |
| Notifications | Amazon SNS | Email alerts for high-risk students |
| Security | AWS IAM | Least-privilege access control |


#### Dataset

The workshop uses a dataset of ~3,000 student records containing academic and behavioral features (attendance, assignment and exam scores, class participation, homework submission, digital learning hours, extracurricular participation, and a behavioral engagement score) with a binary `at_risk` label used as the prediction target.

![Dataset preview]( /fcj-workshop-template/images/5-Workshop/5.1-Workshop-overview/dataset-preview.png)

#### Region

This workshop uses the **Asia Pacific (Singapore) `ap-southeast-1`** region. Make sure every resource (S3, Lambda, DynamoDB, API Gateway, SageMaker) is created in the **same region** to avoid cross-region errors.

{{% notice tip %}}
Keep all resources in one region. A common cause of `ResourceNotFoundException` is a Lambda in one region trying to reach a DynamoDB table in another.
{{% /notice %}}