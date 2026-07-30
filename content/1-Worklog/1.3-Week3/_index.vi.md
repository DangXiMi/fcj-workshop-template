---
title: "Week 3 Worklog"
date: 2026-06-29
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu Tuần 3:

* Phát triển kỹ năng về phân tích dữ liệu và business intelligence trên AWS.
* Làm chủ phân tích serverless với Amazon Athena.
* Hiểu AWS Glue cho ETL và Data Catalog.
* Tạo bảng điều khiển (dashboard) trực quan với Amazon QuickSight.
* Khám phá PostgreSQL nâng cao trên AWS.

### Nhiệm vụ thực hiện trong tuần:

| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | ---- | ---------- | --------------- | ------------------ |
| 1 | **Tổng quan các dịch vụ Data Analytics:** <br>&emsp; + So sánh Athena, Glue, EMR, Redshift, QuickSight <br>&emsp; + Hiểu use case phù hợp cho từng dịch vụ | 29/06/2026 | 29/06/2026 | Analytics Module |
| 2 | **Phân tích Serverless với Amazon Athena:** <br>&emsp; + Tạo bảng Athena từ dữ liệu trên S3 <br>&emsp; + Viết câu truy vấn SQL trên dữ liệu CSV/Parquet/JSON <br>&emsp; + Phân vùng dữ liệu để tối ưu hiệu năng | 30/06/2026 | 30/06/2026 | Athena Workshop |
| 3 | **AWS Glue:** <br>&emsp; + Crawler và Data Catalog <br>&emsp; + ETL job với PySpark/Spark <br>&emsp; + Job bookmark và lập lịch | 01/07/2026 | 01/07/2026 | Glue Documentation |
| 4 | **Business Intelligence với Amazon QuickSight:** <br>&emsp; + Kết nối với Athena và S3 <br>&emsp; + Xây dựng biểu đồ và dashboard <br>&emsp; + Chia sẻ kết quả với các bên liên quan | 02/07/2026 | 02/07/2026 | QuickSight Workshop |
| 5 | **Advanced PostgreSQL trên AWS – Phần 1:** <br>&emsp; + PostgreSQL managed với Amazon RDS <br>&emsp; + Tinh chỉnh hiệu năng và giám sát <br>&emsp; + Read Replica và Multi‑AZ deployment | 03/07/2026 | 03/07/2026 | PostgreSQL Series |
| 6 | **Advanced PostgreSQL trên AWS – Phần 2:** <br>&emsp; + Chiến lược migration (DMS) <br>&emsp; + High Availability và Disaster Recovery <br>&emsp; + Extension và Stored Procedure | 04/07/2026 | 04/07/2026 | PostgreSQL Series |

### Thành tựu đạt được Tuần 3:

#### ✅ Nền tảng Data Analytics
* Hiểu hệ sinh thái analytics của AWS và khi nào nên dùng dịch vụ nào.
* Tạo truy vấn Athena để phân tích dữ liệu lưu trên S3.
* Tối ưu truy vấn bằng partitioning và bucketing.
* Tích hợp Athena với QuickSight cho báo cáo ad‑hoc.

#### ✅ AWS Glue ETL
* Thiết lập Glue Data Catalog bằng cách chạy crawler.
* Viết ETL job bằng PySpark để biến đổi dữ liệu (lọc, gộp, tổng hợp).
* Tự động hóa job với trigger và lịch trình.
* Sử dụng job bookmark để xử lý dữ liệu gia tăng.

#### ✅ Amazon QuickSight
* Kết nối Athena làm nguồn dữ liệu.
* Tạo dashboard tương tác với:
  - Biểu đồ cột, đường, heat map.
  - Bộ lọc và tham số cho người dùng tùy chỉnh.
  - Trường tính toán và hàm tổng hợp.
* Xuất bản dashboard và chia sẻ với team.

#### ✅ PostgreSQL trên AWS
* Khởi chạy RDS PostgreSQL ở môi trường production.
* Cấu hình Multi‑AZ cho High Availability.
* Thiết lập Read Replica để scale đọc.
* Giám sát hiệu năng bằng Performance Insights và CloudWatch.
* Khám phá các extension phổ biến: `pg_stat_statements`, `postgis`.

### Bài học kinh nghiệm chính:

> **Điểm nhấn:** Phân tích dữ liệu đóng vai trò then chốt trong các dự án AI, giúp hiểu chất lượng dữ liệu, khám phá xu hướng và theo dõi hiệu suất model. Các công cụ serverless như Athena và Glue cho phép phân tích với chi phí thấp mà không cần quản lý hạ tầng.