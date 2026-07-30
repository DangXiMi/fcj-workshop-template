---
title: "Ingestion Lambda & S3 Trigger"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 5.3.3. </b> "
---

#### Create the Lambda

1. **Lambda → Create function**.
2. Function name: `uploadDatasetFunction`.
3. Runtime: **Python 3.12**.
4. Execution role: **Use an existing role → `StudentWarningLambdaRole`**.

#### Package with dependencies

This function needs `pandas`, so it must be deployed as a ZIP package with dependencies. Keep the package lightweight — **do not** bundle scikit-learn here.

```bash
mkdir build
pip install boto3 pandas -t build/
copy backend/lambda/upload_dataset/lambda_function.py build/
cd build
Compress-Archive * upload_dataset.zip
```

Upload via **Code → Upload from → .zip file**, then **Deploy**.

#### Function code (excerpt)

```python
import json
import boto3
import pandas as pd

s3 = boto3.client("s3")
dynamodb = boto3.resource("dynamodb")
table = dynamodb.Table("student_records")

def lambda_handler(event, context):
    bucket = event["Records"][0]["s3"]["bucket"]["name"]
    key = event["Records"][0]["s3"]["object"]["key"]
    obj = s3.get_object(Bucket=bucket, Key=key)
    df = pd.read_csv(obj["Body"])

    for _, row in df.iterrows():
        table.put_item(Item={
            "student_id": str(row["student_id"]),
            "attendance_rate": float(row["attendance_rate"]),
            "assignment_avg_score": float(row["assignment_avg_score"]),
            "exam_avg_score": float(row["exam_avg_score"]),
            "class_participation": float(row["class_participation"]),
            "homework_submission_rate": float(row["homework_submission_rate"]),
            "at_risk": int(row["at_risk"]),
        })
    return {"statusCode": 200, "body": json.dumps("Dataset processed successfully")}
```

#### Increase timeout

The dataset has ~3,000 rows. Under **Configuration → General configuration**, set:

- Timeout: **1 minute**
- Memory: **512 MB**

#### Add the S3 trigger

1. In the Lambda designer, click **Add trigger → S3**.
2. Bucket: `student-warning-system`.
3. Event type: **All object create events**.
4. Prefix: `raw-data/`.
5. Acknowledge and **Add**.

![S3 trigger]( /images/5-Workshop/5.3-Backend-Pipeline/s3-trigger.png)

#### Test end-to-end

Upload `student_performance.csv` into `raw-data/`. Then verify:

- **CloudWatch Logs** show `Dataset processed successfully`.
- **DynamoDB → student_records** contains the records.

![CloudWatch logs success]( /images/5-Workshop/5.3-Backend-Pipeline/cloudwatch-ingest.png)