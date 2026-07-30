---
title: "Batch Prediction Lambda"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 5.5.2. </b> "
---

Create `predictRiskFunction`. It reads the CSV, calls the SageMaker endpoint in batches, writes results to `prediction_results`, and sends an SNS summary of high-risk students.

#### Key design points

- **Feature order** must match training exactly.
- Call the endpoint in **batches** (e.g. 500 rows) rather than one row at a time, to avoid timeouts on ~3,000 records.
- Write results to DynamoDB with `batch_writer()`.
- Send the SNS alert only when high-risk students exist.

#### Environment variables

```text
SAGEMAKER_ENDPOINT = <endpoint-name>
PREDICTION_TABLE   = prediction_results
THRESHOLD          = 0.5
SNS_TOPIC_ARN      = <topic-arn>   # optional
BATCH_SIZE         = 500
```

#### IAM permissions

The role needs, scoped least-privilege where possible:

- `sagemaker:InvokeEndpoint`
- `dynamodb:BatchWriteItem` / `PutItem` on `prediction_results`
- `sns:Publish` on the alert topic

{{% notice info %}}
If you see `AccessDeniedException` on `BatchWriteItem`, the role is missing the DynamoDB write permission. If you see `ResourceNotFoundException`, the `prediction_results` table does not exist or is in another region.
{{% /notice %}}

#### Test

Upload a small CSV, then confirm:

- CloudWatch: `Saved N predictions to prediction_results`.
- DynamoDB `prediction_results` contains items with `prediction` and `probability`.
- An SNS email arrives if high-risk students were found.

![Prediction results in DynamoDB]( /images/5-Workshop/5.5-ML/prediction-results.png)