---
title: "Dọn dẹp tài nguyên"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 5.7. </b> "
---

Chỉ thực hiện dọn dẹp **sau khi** bạn đã chụp đầy đủ các hình ảnh minh chứng và hoàn thành xong bài trình diễn (demo) — các tài nguyên sẽ không thể chụp lại sau khi đã xóa.

{{% notice warning %}}
Xóa **SageMaker endpoint đầu tiên**. Đây là tài nguyên đắt tiền nhất và tính phí liên tục trong suốt thời gian chạy.
{{% /notice %}}

#### Thứ tự xóa tài nguyên

1. **SageMaker** — xóa endpoint, cấu hình endpoint (endpoint config) và mô hình (model).
2. **Lambda** — xóa tất cả các hàm (`uploadDatasetFunction`, `getStudentsFunction`, `predictRiskFunction`, `predictRiskOnDemand`, `create/update/deleteStudentFunction`, `getPredictionsFunction`).
3. **API Gateway** — xóa API `student-warning-api`.
4. **DynamoDB** — xóa các bảng `student_records` và `prediction_results`.
5. **S3** — dọn rác (empty) và xóa các bucket chứa tập dữ liệu và frontend.
6. **CloudFront** — vô hiệu hóa (disable), sau đó xóa distribution.
7. **CloudWatch** — xóa các cảnh báo (alarms) và các nhóm nhật ký (log groups).
8. **SNS** — xóa topic và đăng ký nhận tin (subscription).
9. **IAM** — xóa các role và chính sách (policy) đã tạo cho workshop này.

#### Kiểm tra lại

Xác nhận tại mục **Billing → Cost Explorer** để đảm bảo không còn chi phí phát sinh ngoài ý muốn sau khi dọn dẹp.


#### Những gì chúng ta đã xây dựng

Chúng ta đã triển khai thành công một Hệ thống Thông tin Cloud-native hoàn chỉnh: đường ống dữ liệu serverless, REST API, bảng điều khiển React DSS trên CloudFront, luồng dự báo rủi ro dựa trên ML với SageMaker, cảnh báo tự động qua SNS và giám sát với CloudWatch — bao quát toàn bộ các khía cạnh về kiến trúc, triển khai, tích hợp ML, giám sát, bảo mật, tối ưu chi phí, kiểm thử và dọn dẹp tài nguyên.