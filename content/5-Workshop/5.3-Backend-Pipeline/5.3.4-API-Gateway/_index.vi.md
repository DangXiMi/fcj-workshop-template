---
title: "Tạo Read API với API Gateway"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 5.3.4. </b> "
---

#### Tạo Lambda đọc dữ liệu

Tạo hàm `getStudentsFunction` (Python 3.12, role `StudentWarningLambdaRole`). DynamoDB trả về các số dưới dạng kiểu `Decimal` (không thể tuần hoàn hóa sang JSON trực tiếp), do đó cần chuyển đổi chúng và trả về CORS headers trực tiếp trong hàm (yêu cầu bắt buộc đối với tích hợp Lambda proxy).

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

#### Tạo REST API

1. Truy cập **API Gateway → Create API → REST API → Build**.
2. Tên API (API name): `student-warning-api`.
3. Chọn **Create resource** → đường dẫn (path) `/students`.
4. Tại tài nguyên `/students`, chọn **Create method → GET**.
5. Loại tích hợp (Integration type): **Lambda**, bật tùy chọn **Lambda proxy integration**, chọn hàm `getStudentsFunction`.

{{% notice warning %}}
Khi sử dụng **Lambda proxy integration**, API Gateway sẽ trả về chính xác những gì hàm Lambda phản hồi. Các CORS headers phải được tạo bên trong code của Lambda, chứ không phải ở bảng "Integration response" của API Gateway (bảng này bị vô hiệu hóa đối với chế độ proxy).
{{% /notice %}}

#### Triển khai API (Deploy)

Chọn **Deploy API → Stage `dev`**. Đây là bước bắt buộc; nếu không thực hiện, các yêu cầu sẽ trả về lỗi `403 Missing Authentication Token`.

Đường dẫn Invoke URL thu được:

```text
https://<api-id>.execute-api.ap-southeast-1.amazonaws.com/dev/students
```

#### Kiểm thử

```bash
curl -i https://<api-id>.execute-api.ap-southeast-1.amazonaws.com/dev/students
```

Kết quả mong đợi: `200 OK`, một mảng JSON và header `Access-Control-Allow-Origin: *`.

![API test 200 OK]( /images/5-Workshop/5.3-Backend-Pipeline/api-test.png)