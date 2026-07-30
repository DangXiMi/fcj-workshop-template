---
title: "CloudWatch Alarms"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 5.6.2. </b> "
---

Create alarms for the key Lambdas and the API, wired to the SNS topic.

| Metric | Scope | Threshold |
|--------|-------|-----------|
| `Errors` (Sum) | each Lambda | > 0 |
| `Duration` (Max) | each Lambda | near timeout |
| `5XXError` | API Gateway | > 0 |

Steps:

1. **CloudWatch → Alarms → Create alarm → Select metric**.
2. Choose the metric (e.g. Lambda → `Errors`).
3. Set threshold and period.
4. Alarm action: notify the SNS topic.

Trigger a deliberate error (e.g. malformed `POST /predict`) to move the alarm to **In alarm** and confirm the email. 

![CloudWatch alarm]( /images/5-Workshop/5.6-Monitoring/alarm.png)