---
title: "Clean up"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 5.7. </b> "
---

Clean up **after** you have captured all screenshots and completed the demo — resources cannot be re-captured once deleted.

{{% notice warning %}}
Delete the **SageMaker endpoint first**. It is the most expensive resource and is billed continuously while running.
{{% /notice %}}

#### Deletion order

1. **SageMaker** — delete the endpoint, endpoint config, and model.
2. **Lambda** — delete all functions (`uploadDatasetFunction`, `getStudentsFunction`, `predictRiskFunction`, `predictRiskOnDemand`, `create/update/deleteStudentFunction`, `getPredictionsFunction`).
3. **API Gateway** — delete `student-warning-api`.
4. **DynamoDB** — delete `student_records` and `prediction_results`.
5. **S3** — empty and delete the dataset and frontend buckets.
6. **CloudFront** — disable, then delete the distribution.
7. **CloudWatch** — delete alarms and log groups.
8. **SNS** — delete the topic and subscription.
9. **IAM** — delete the roles and policies created for this workshop.

#### Verify

Confirm in **Billing → Cost Explorer** that no unexpected charges continue after cleanup.


#### What we built

We deployed a complete cloud-native Information System: a serverless data pipeline, a REST API, a React DSS dashboard on CloudFront, ML-based risk prediction with SageMaker, automated SNS alerts, and CloudWatch monitoring — covering architecture, deployment, ML integration, monitoring, security, cost optimization, testing, and cleanup.