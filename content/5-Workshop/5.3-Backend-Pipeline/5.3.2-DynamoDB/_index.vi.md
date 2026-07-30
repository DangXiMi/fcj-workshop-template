---
title: "Tạo Bảng DynamoDB"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 5.3.2. </b> "
---

Tạo hai bảng ở chế độ dung lượng **On-demand** (tối ưu hóa chi phí).

| Bảng | Khóa phân vùng (Partition key) | Mục đích |
|-------|---------------|---------|
| `student_records` | `student_id` (String) | Dữ liệu học tập của sinh viên |
| `prediction_results` | `student_id` (String) | Kết quả dự báo từ mô hình ML |

Các bước thực hiện cho từng bảng:

1. Truy cập **DynamoDB → Create table**.
2. Nhập tên bảng và khóa phân vùng `student_id` (Kiểu String).
3. Chế độ dung lượng (Capacity mode): **On-demand**.
4. Chọn **Create table**.

![DynamoDB tables]( /images/5-Workshop/5.3-Backend-Pipeline/dynamodb-tables.png)