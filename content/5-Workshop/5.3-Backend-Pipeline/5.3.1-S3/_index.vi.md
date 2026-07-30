---
title: "Tạo S3 Buckets"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 5.3.1. </b> "
---

Tạo một bucket **riêng tư (private)** để chứa tập dữ liệu và các thành phần mô hình ML (model artifacts).

1. Truy cập **S3 → Create bucket**.
2. Tên Bucket (Bucket name): `student-warning-system` (phải là duy nhất trên toàn cầu — hãy thêm hậu tố nếu tên đã bị trùng).
3. Vùng (Region): `ap-southeast-1`.
4. Giữ tùy chọn **Block all public access = ON** (tập dữ liệu bắt buộc phải duy trì ở chế độ riêng tư).

Tạo các tiền tố (thư mục) sau:

```text
raw-data/          # đầu vào cho quá trình nạp dữ liệu
frontend/          # lưu trữ bản đóng gói frontend (dist)
model/             # các tệp mô hình ML
```


![S3 bucket structure]( /fcj-workshop-template/images/5-Workshop/5.3-Backend-Pipeline/s3-structure.png)