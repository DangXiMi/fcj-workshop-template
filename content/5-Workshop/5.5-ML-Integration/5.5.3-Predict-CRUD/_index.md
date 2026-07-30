---
title: "On-Demand Prediction & CRUD APIs"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 5.5.3. </b> "
---

Add four Lambda functions and their API routes. These only use `boto3`, so they can be pasted inline (no heavy ZIP).

| Method | Resource | Lambda | Purpose |
|--------|----------|--------|---------|
| POST | `/predict` | `predictRiskOnDemand` | Predict one student without saving |
| POST | `/students` | `createStudentFunction` | Create student + predict |
| PUT | `/students/{student_id}` | `updateStudentFunction` | Update student |
| DELETE | `/students/{student_id}` | `deleteStudentFunction` | Delete student |

All use **Lambda proxy integration**, so each function returns CORS headers matching its method (e.g. `POST,OPTIONS`).

#### On-demand predict handler (excerpt)

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

#### Deploy and test

Create the resources/methods, then **Deploy API → dev**. Test with Postman:

```json
POST /dev/predict
{ "attendance_rate": 60, "assignment_avg_score": 45, "exam_avg_score": 40,
  "homework_submission_rate": 50, "class_participation": 3 }
→ { "at_risk": 1, "probability": 0.98 }
```


![On-demand prediction]( /fcj-workshop-template/images/5-Workshop/5.5-ML/ondemand-predict.png)