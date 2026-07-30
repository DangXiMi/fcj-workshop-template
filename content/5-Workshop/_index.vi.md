---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
includeInReport: false
---


# Hệ thống Cảnh báo sớm Kết quả Học tập của Sinh viên trên AWS

#### Tổng quan

**Hệ thống Cảnh báo sớm Kết quả Học tập của Sinh viên (Student Performance Early Warning System - SP-EWS)** là một Hệ thống Thông tin Cloud-native được xây dựng hoàn toàn trên nền tảng AWS. Hệ thống này nạp dữ liệu về học tập và hành vi của sinh viên, tự động dự báo sinh viên nào đang có nguy cơ học tập kém bằng mô hình Machine Learning, và hiển thị kết quả thông qua một bảng điều khiển (dashboard) theo dạng Hệ thống Hỗ trợ Ra quyết định (Decision-Support-System - DSS) đi kèm với tính năng tự động gửi cảnh báo qua email cho các sinh viên có nguy cơ cao.

Trong workshop này, bạn sẽ tự tay xây dựng hệ thống từ đầu đến cuối (end-to-end) bằng cách sử dụng các dịch vụ serverless và managed của AWS. Bạn sẽ bắt đầu từ một tài khoản AWS trống và lần lượt triển khai:

+ Một **đường ống dữ liệu serverless (serverless data pipeline)** giúp nạp tập dữ liệu CSV vào DynamoDB.
+ Một **REST API** được xây dựng bằng API Gateway và Lambda.
+ Một **bảng điều khiển React (React dashboard)** được lưu trữ trên Amazon S3 và phân phối qua Amazon CloudFront.
+ Một **luồng xử lý dự báo Machine Learning (ML inference workflow)** sử dụng endpoint của Amazon SageMaker (XGBoost) cho cả dự báo theo đợt (batch) và theo yêu cầu (on-demand).
+ **Hệ thống gửi cảnh báo qua email** với Amazon SNS và **mức độ quan sát được (observability)** với Amazon CloudWatch.
+ Quy trình **dọn dẹp (cleanup)** hoàn chỉnh để tránh phát sinh chi phí không mong muốn.

Dự án tuân thủ theo Khung chuẩn Kiến trúc Tối ưu của AWS (AWS Well-Architected Framework), bao hàm toàn bộ các khía cạnh từ kiến trúc, triển khai, tích hợp ML, giám sát, bảo mật, tối ưu chi phí, kiểm thử cho đến dọn dẹp tài nguyên.

{{< figure src="/images/5-Workshop/5.1-Workshop-overview/Solution_Archi.jpg" width="800" >}}

#### Nội dung

1. [Tổng quan Workshop](5.1-workshop-overview/)
2. [Các điều kiện tiên quyết](5.2-prerequiste/)
3. [Core Backend & Đường ống dữ liệu](5.3-Backend-Pipeline/)
4. [Frontend Dashboard & CloudFront](5.4-Frontend-CloudFront/)
5. [Tích hợp Machine Learning](5.5-ML-Integration/)
6. [Giám sát & Cảnh báo](5.6-Monitoring-Alerts/)
7. [Dọn dẹp tài nguyên](5.7-Cleanup/)