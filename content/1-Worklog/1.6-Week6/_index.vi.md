---
title: "Week 6 Worklog"
date: 2026-07-20
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu Tuần 6:

* Triển khai CI/CD cho ứng dụng AI/ML sử dụng AWS CodePipeline.
* Tự động hóa việc build, test và triển khai model ML.
* Tích hợp với AWS CodeBuild và CodeDeploy.
* Hiểu các thực hành DevOps cho MLOps.

### Nhiệm vụ thực hiện trong tuần:

| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | ---- | ---------- | --------------- | ------------------ |
| 1 | **CI/CD Pipeline với AWS CodePipeline:** <br>&emsp; + Stage Source (CodeCommit, GitHub) <br>&emsp; + Stage Build (CodeBuild) <br>&emsp; + Stage Deploy (CodeDeploy hoặc custom) | 20/07/2026 | 20/07/2026 | CodePipeline Docs |
| 2 | **Triển khai tự động với AWS CodePipeline:** <br>&emsp; + Tích hợp với SageMaker Pipelines <br>&emsp; + Kích hoạt retraining khi dữ liệu thay đổi <br>&emsp; + Triển khai model mới lên endpoint | 21/07/2026 | 21/07/2026 | CI/CD Workshop |
| 3 | **DevOps với AWS CodePipeline:** <br>&emsp; + Sử dụng pipeline variable và artifact <br>&emsp; + Thêm manual approval gate <br>&emsp; + Thông báo và giám sát | 22/07/2026 | 22/07/2026 | DevOps with CodePipeline |
| 4 | **Hạ tầng như mã với AWS CloudFormation:** <br>&emsp; + Thiết kế và triển khai stack <br>&emsp; + Sử dụng Parameter, Output, Condition <br>&emsp; + Quản lý cập nhật và rollback | 23/07/2026 | 23/07/2026 | CloudFormation |
| 5 | **AWS CDK Essentials:** <br>&emsp; + Định nghĩa hạ tầng bằng TypeScript/Python <br>&emsp; + Tạo construct tái sử dụng <br>&emsp; + Triển khai stack với CDK CLI | 24/07/2026 | 24/07/2026 | CDK Workshop |
| 6 | **Infrastructure as Code cho ECS với CDK:** <br>&emsp; + Triển khai ứng dụng ML đóng gói container <br>&emsp; + Sử dụng CDK Pipelines cho CI/CD | 25/07/2026 | 25/07/2026 | CDK for ECS |

### Thành tựu đạt được Tuần 6:

#### ✅ CI/CD với CodePipeline
* Thiết lập pipeline với source (CodeCommit), build (CodeBuild) và deploy.
* Tích hợp CodeBuild với Docker để build và push container.
* Triển khai ứng dụng container lên ECS/Fargate và SageMaker endpoint.
* Thêm manual approval cho giai đoạn production.

#### ✅ Tự động hóa luồng ML
* Kích hoạt SageMaker Pipeline từ CodePipeline khi có dữ liệu mới.
* Sử dụng artifact để truyền model giữa các stage.
* Tự động triển khai model đã được phê duyệt lên staging và production.

#### ✅ Hạ tầng như mã (IaC)
* Học CloudFormation: template, stack, drift detection.
* Tạo CloudFormation template cho:
  - VPC, subnet, security group.
  - SageMaker endpoint và IAM role.
  - Lambda và API Gateway.
* Chuyển sang AWS CDK:
  - Định nghĩa stack bằng Python.
  - Sử dụng L2 construct để trừu tượng hóa cao hơn.
  - Synthesize và deploy stack.

#### ✅ CDK Pipelines
* Xây dựng pipeline CI/CD bằng CDK Pipelines.
* Triển khai đa môi trường (dev → test → prod).
* Tự động cung cấp hạ tầng sau mỗi lần commit.

### Bài học kinh nghiệm chính:

> **Điểm nhấn:** CI/CD và IaC là yếu tố then chốt cho việc triển khai ML đáng tin cậy và lặp lại. Sử dụng CodePipeline và CDK cho phép team xem model ML như mã nguồn, với quy trình versioning, kiểm thử và triển khai tự động, giảm thiểu lỗi thủ công và tăng tốc độ phát hành.