---
title: "Read API with API Gateway"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 5.3.4. </b> "
---

#### Create the read Lambda

Create `getStudentsFunction` (Python 3.12, `StudentWarningLambdaRole`). DynamoDB returns numbers as `Decimal`, which is not JSON-serializable, so convert them and return CORS headers directly (required for Lambda proxy integration).

```python
import json
import boto3
from decimal import Decimal

dynamodb = boto3.resource("dynamodb")
table = dynamodb.Table("student_records")

def convert_decimal(obj):
    if isinstance(obj, list):
        return [convert_decimal(i) for i in obj]
    if isinstance(obj, dict):
        return {k: convert_decimal(v) for k, v in obj.items()}
    if isinstance(obj, Decimal):
        return int(obj) if obj % 1 == 0 else float(obj)
    return obj

def lambda_handler(event, context):
    items = table.scan()["Items"]
    return {
        "statusCode": 200,
        "headers": {
            "Content-Type": "application/json",
            "Access-Control-Allow-Origin": "*",
            "Access-Control-Allow-Methods": "GET,OPTIONS",
            "Access-Control-Allow-Headers": "Content-Type",
        },
        "body": json.dumps(convert_decimal(items)),
    }
```

#### Create the REST API

1. **API Gateway → Create API → REST API → Build**.
2. API name: `student-warning-api`.
3. **Create resource** → path `/students`.
4. On `/students`, **Create method → GET**.
5. Integration type: **Lambda**, enable **Lambda proxy integration**, select `getStudentsFunction`.

{{% notice warning %}}
With **Lambda proxy integration**, API Gateway returns exactly what Lambda returns. CORS headers must be produced inside the Lambda, not in the API Gateway "Integration response" panel (which is disabled for proxy).
{{% /notice %}}

#### Deploy

**Deploy API → Stage `dev`**. This is mandatory; otherwise requests return `403 Missing Authentication Token`.

Invoke URL:

```text
https://<api-id>.execute-api.ap-southeast-1.amazonaws.com/dev/students
```

#### Test

```bash
curl -i https://<api-id>.execute-api.ap-southeast-1.amazonaws.com/dev/students
```

Expected: `200 OK`, a JSON array, and `Access-Control-Allow-Origin: *` in the headers.

![API test 200 OK]( /fcj-workshop-template/images/5-Workshop/5.3-Backend-Pipeline/api-test.png)