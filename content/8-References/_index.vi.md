---
title: "Tài liệu tham khảo"
date: 2024-01-01
weight: 8
chapter: false
pre: " <b> 8.  </b> "
---

Trang này liệt kê các tài liệu chính thức, framework, thư viện và nguồn tài liệu cộng đồng đã được tham khảo xuyên suốt nhật ký công việc thực tập và quá trình triển khai AWS Workshop.

### Repository của dự án

Toàn bộ mã nguồn của dự án này (backend, frontend, hạ tầng, và báo cáo này) được lưu trữ tại:
<https://github.com/cucSdatJ/student-warning-system>


### Tài liệu chính thức AWS

| # | Dịch vụ | Link |
| --- | ------- | ---- |
| 1 | AWS Identity and Access Management (IAM) | <https://docs.aws.amazon.com/IAM/> |
| 2 | Amazon S3 | <https://docs.aws.amazon.com/AmazonS3/> |
| 3 | Amazon S3 – Static Website Hosting | <https://docs.aws.amazon.com/AmazonS3/latest/userguide/WebsiteHosting.html> |
| 4 | AWS Lambda | <https://docs.aws.amazon.com/lambda/> |
| 5 | AWS Lambda – Python Deployment Packages | <https://docs.aws.amazon.com/lambda/latest/dg/python-package.html> |
| 6 | Amazon DynamoDB | <https://docs.aws.amazon.com/dynamodb/> |
| 7 | Amazon API Gateway | <https://docs.aws.amazon.com/apigateway/> |
| 8 | Amazon API Gateway – Enabling CORS | <https://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-cors.html> |
| 9 | Amazon SageMaker | <https://docs.aws.amazon.com/sagemaker/> |
| 10 | Amazon SageMaker – Real-Time Endpoints | <https://docs.aws.amazon.com/sagemaker/latest/dg/realtime-endpoints.html> |
| 11 | Amazon CloudFront | <https://docs.aws.amazon.com/cloudfront/> |
| 12 | Amazon CloudWatch | <https://docs.aws.amazon.com/cloudwatch/> |
| 13 | Amazon SNS | <https://docs.aws.amazon.com/sns/> |
| 14 | AWS CLI | <https://docs.aws.amazon.com/cli/> |

### Framework & Best Practices của AWS

| # | Tài nguyên | Link |
| --- | -------- | ---- |
| 1 | AWS Well-Architected Framework | <https://aws.amazon.com/architecture/well-architected/> |

### Machine Learning & Xử lý dữ liệu

| # | Thư viện | Link |
| --- | ------- | ---- |
| 1 | scikit-learn | <https://scikit-learn.org/stable/> |
| 2 | scikit-learn – Model Evaluation | <https://scikit-learn.org/stable/modules/model_evaluation.html> |
| 3 | pandas | <https://pandas.pydata.org/> |

### Frontend & Công cụ

| # | Công cụ | Link |
| --- | ---- | ---- |
| 1 | Vite | <https://vitejs.dev/> |
| 2 | Recharts | <https://recharts.org/> |

### Tài nguyên chương trình & cộng đồng

| # | Tài nguyên | Link |
| --- | -------- | ---- |
| 1 | Cloud Journey – Tài liệu chương trình FCAJ | <https://cloudjourney.awsstudygroup.com/> |
| 2 | AWS Study Group – Blog | <https://awsstudygroup.com> |
| 3 | AWS Study Group – Nhóm Facebook | <https://www.facebook.com/groups/awsstudygroupfcj> |

### Bộ dữ liệu

Bộ dữ liệu kết quả học tập sinh viên (~3.000 bản ghi) sử dụng xuyên suốt workshop được chuẩn bị tổng hợp (synthetic) riêng cho dự án này, bao gồm các feature về học tập và hành vi (điểm danh, điểm bài tập/thi, mức độ tham gia lớp học, tỷ lệ nộp bài tập về nhà, số giờ học trực tuyến, mức độ tham gia ngoại khóa, và điểm tương tác hành vi) cùng nhãn nhị phân `at_risk`.