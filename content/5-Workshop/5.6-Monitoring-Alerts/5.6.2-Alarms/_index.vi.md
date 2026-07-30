---
title: "CloudWatch Alarms"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 5.6.2. </b> "
---

Tạo các cảnh báo (alarms) cho các hàm Lambda quan trọng và API, sau đó kết nối đến SNS topic.

| Chỉ số (Metric) | Phạm vi (Scope) | Ngưỡng (Threshold) |
|--------|-------|-----------|
| `Errors` (Sum) | từng hàm Lambda | > 0 |
| `Duration` (Max) | từng hàm Lambda | gần chạm ngưỡng timeout |
| `5XXError` | API Gateway | > 0 |

Các bước thực hiện:

1. Truy cập **CloudWatch → Alarms → Create alarm → Select metric**.
2. Chọn chỉ số mong muốn (ví dụ: Lambda → `Errors`).
3. Thiết lập ngưỡng và chu kỳ (period).
4. Hành động cảnh báo (Alarm action): gửi thông báo đến SNS topic.

Tạo một lỗi cố ý (ví dụ: gửi dữ liệu sai định dạng đến `POST /predict`) để chuyển trạng thái cảnh báo sang **In alarm** và xác nhận email đã được gửi.

![CloudWatch alarm]( /fcj-workshop-template/images/5-Workshop/5.6-Monitoring/alarm.png)