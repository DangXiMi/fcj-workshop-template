---
title: "Hàm Lambda Nạp Dữ Liệu & S3 Trigger"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 5.3.3. </b> "
---

#### Tạo hàm Lambda

1. Truy cập **Lambda → Create function**.
2. Tên hàm (Function name): `uploadDatasetFunction`.
3. Môi trường thực thi (Runtime): **Python 3.12**.
4. Role thực thi (Execution role): **Use an existing role → `StudentWarningLambdaRole`**.

#### Đóng gói kèm thư viện phụ thuộc (dependencies)

Hàm này cần thư viện `pandas`, vì vậy nó phải được triển khai dưới dạng tệp ZIP đóng gói kèm thư viện. Hãy giữ gói triển khai gọn nhẹ — **không** đóng gói thư viện scikit-learn ở đây.

```bash
mkdir build
pip install boto3 pandas -t build/
copy backend/lambda/upload_dataset/lambda_function.py build/
cd build
Compress-Archive * upload_dataset.zip
```

Tải tệp lên qua mục **Code → Upload from → .zip file**, sau đó nhấn **Deploy**.

#### Mã nguồn hàm Lambda (trích đoạn)

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

#### Tăng thời gian chờ (Timeout)

Tập dữ liệu có ~3.000 dòng. Tại mục **Configuration → General configuration**, hãy thiết lập:

- Thời gian chờ (Timeout): **1 minute**
- Bộ nhớ (Memory): **512 MB**

#### Thêm S3 trigger

1. Trong giao diện thiết kế Lambda, chọn **Add trigger → S3**.
2. Bucket: `student-warning-system`.
3. Loại sự kiện (Event type): **All object create events**.
4. Tiền tố (Prefix): `raw-data/`.
5. Xác nhận và chọn **Add**.

![S3 trigger]( /images/5-Workshop/5.3-Backend-Pipeline/s3-trigger.png)

#### Kiểm thử end-to-end

Tải tệp `student_performance.csv` vào thư mục `raw-data/`. Sau đó kiểm tra:

- **CloudWatch Logs** hiển thị `Dataset processed successfully`.
- **DynamoDB → student_records** đã nạp đầy đủ các bản ghi.

![CloudWatch logs success]( /images/5-Workshop/5.3-Backend-Pipeline/cloudwatch-ingest.png)