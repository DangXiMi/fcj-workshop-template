---
title: "Core Backend & Đường ống dữ liệu"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---

Trong phần này, chúng ta sẽ xây dựng đường ống dữ liệu serverless: bộ lưu trữ S3, các bảng DynamoDB, hàm Lambda nạp dữ liệu và API đọc dữ liệu.

```
Tải lên CSV → S3 (raw-data/) → Lambda → DynamoDB → API Gateway
```

#### Nội dung

1. [Tạo S3 Buckets](5.3.1-S3/)
2. [Tạo Bảng DynamoDB](5.3.2-DynamoDB/)
3. [Hàm Lambda Nạp Dữ Liệu & S3 Trigger](5.3.3-Ingest-Lambda/)
4. [Tạo Read API với API Gateway](5.3.4-API-Gateway/)