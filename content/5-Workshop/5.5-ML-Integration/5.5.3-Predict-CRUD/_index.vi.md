---
title: "Dự Báo Theo Yêu Cầu & Các API CRUD"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 5.5.3. </b> "
---

Thêm 4 hàm Lambda cùng các tuyến đường API tương ứng. Các hàm này chỉ sử dụng thư viện `boto3`, vì vậy có thể dán trực tiếp mã nguồn vào giao diện điều khiển (không cần đóng gói file ZIP nặng).

| Phương thức | Tài nguyên | Hàm Lambda | Mục đích |
|--------|----------|--------|---------|
| POST | `/predict` | `predictRiskOnDemand` | Dự báo cho một sinh viên mà không lưu vào CSDL |
| POST | `/students` | `createStudentFunction` | Tạo sinh viên mới + chạy dự báo |
| PUT | `/students/{student_id}` | `updateStudentFunction` | Cập nhật thông tin sinh viên |
| DELETE | `/students/{student_id}` | `deleteStudentFunction` | Xóa sinh viên |

Tất cả đều sử dụng **Lambda proxy integration**, vì vậy mỗi hàm phải trả về các CORS headers phù hợp với phương thức tương ứng (ví dụ: `POST,OPTIONS`).

#### Hàm xử lý dự báo theo yêu cầu (trích đoạn)

```python
FEATURE_KEYS = ["attendance_rate", "assignment_avg_score", "exam_avg_score",
                "homework_submission_rate", "class_participation"]

def lambda_handler(event, context):
    data = json.loads(event.get("body") or "{}")
    features = [float(data[k]) for k in FEATURE_KEYS]
    csv_body = ",".join(str(f) for f in features)
    r = sagemaker.invoke_endpoint(EndpointName=ENDPOINT, ContentType="text/csv", Body=csv_body)
    prob = float(r["Body"].read().decode().strip())
    return _resp(200, {"at_risk": 1 if prob >= THRESHOLD else 0,
                       "probability": round(prob, 4)})
```

#### Triển khai và kiểm thử

Tạo các tài nguyên/phương thức, sau đó chọn **Deploy API → dev**. Kiểm thử bằng Postman:

```json
POST /dev/predict
{ "attendance_rate": 60, "assignment_avg_score": 45, "exam_avg_score": 40,
  "homework_submission_rate": 50, "class_participation": 3 }
→ { "at_risk": 1, "probability": 0.98 }
```


![On-demand prediction]( /images/5-Workshop/5.5-ML/ondemand-predict.png)