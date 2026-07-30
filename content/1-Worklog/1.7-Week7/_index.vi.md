---
title: "Week 7 Worklog"
date: 2026-07-13
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu Tuần 7:

* Làm chủ kiến trúc hướng sự kiện (event‑driven) cho ứng dụng AI.
* Sử dụng Amazon EventBridge để định tuyến sự kiện.
* Xây dựng luồng công việc với AWS Step Functions.
* Triển khai nhắn tin với SQS và SNS.
* Tích hợp tất cả thành một ứng dụng AI gắn kết.

### Nhiệm vụ thực hiện trong tuần:

| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | ---- | ---------- | --------------- | ------------------ |
| 1 | **Amazon EventBridge:** <br>&emsp; + Event bus và rule <br>&emsp; + Event pattern và filter <br>&emsp; + Target (Lambda, Step Functions, SNS) | 13/07/2026 | 13/07/2026 | EventBridge Docs |
| 2 | **AWS Step Functions:** <br>&emsp; + State machine và workflow <br>&emsp; + Các state: Task, Choice, Parallel, Wait <br>&emsp; + Xử lý lỗi và retry | 14/07/2026 | 14/07/2026 | Step Functions Workshop |
| 3 | **Điều phối workflow với Step Functions:** <br>&emsp; + Điều phối luồng ML (chuẩn bị dữ liệu, huấn luyện, triển khai) <br>&emsp; + Tích hợp với SageMaker, Lambda, Glue <br>&emsp; + Giám sát và logging | 15/07/2026 | 15/07/2026 | Step Functions ML |
| 4 | **Nhắn tin với SQS và SNS:** <br>&emsp; + So sánh queue và pub/sub <br>&emsp; + SQS Dead‑Letter Queue và Visibility Timeout <br>&emsp; + SNS Filtering và Fan‑out | 16/07/2026 | 16/07/2026 | SQS/SNS Docs |
| 5 | **Xử lý sự kiện với SQS và SNS (Book Store Series):** <br>&emsp; + Tách rời microservice cho xử lý đơn hàng <br>&emsp; + Sử dụng SQS cho tác vụ bất đồng bộ (xử lý ảnh) <br>&emsp; + Thông báo cho khách hàng qua SNS | 17/07/2026 | 17/07/2026 | Book Store Series – Phần 6 |
| 6 | **Xây dựng AI Pipeline hướng sự kiện:** <br>&emsp; + Kết hợp EventBridge, Step Functions, SQS và AI Services <br>&emsp; + Tạo hệ thống xử lý tài liệu với AI enrichment | 18/07/2026 | 18/07/2026 | Document Management Series |

### Thành tựu đạt được Tuần 7:

#### Amazon EventBridge
* Tạo custom event bus và định nghĩa schema.
* Thiết lập rule để định tuyến event theo pattern.
* Kích hoạt Lambda và Step Functions khi có sự kiện.
* Tích hợp với SaaS bên thứ ba qua partner event.

#### AWS Step Functions
* Thiết kế state machine cho điều phối phức tạp:
  - Xử lý song song nhiều tác vụ.
  - State Choice để rẽ nhánh có điều kiện.
  - State Wait để trì hoãn thực thi.
  - Catch và Retry policy cho khả năng chịu lỗi.
* Tích hợp với SageMaker cho training và inference.
* Sử dụng CloudWatch để giám sát execution.

#### Dịch vụ nhắn tin
* Triển khai SQS queue để tách rời và cân bằng tải.
* Cấu hình Dead‑Letter Queue và cảnh báo khi message tồn đọng.
* Xuất bản lên SNS topic và đăng ký subscriber qua email, SMS, Lambda.
* Sử dụng SNS Filtering để gửi message đến đúng subscriber.

#### Xử lý tài liệu AI hướng sự kiện
* Xây dựng pipeline:
  1. Upload tài liệu lên S3 → EventBridge rule.
  2. Step Functions bắt đầu: trích xuất văn bản, NLP với Comprehend, dịch với Translate, tóm tắt.
  3. Kết quả lưu vào S3 và gửi thông báo qua SNS.
* Sử dụng SQS để xếp hàng các tác vụ xử lý lâu (ví dụ: suy luận ML nặng).

### Bài học kinh nghiệm chính:

> **Điểm nhấn:** Kiến trúc hướng sự kiện và điều phối workflow là chìa khóa để xây dựng ứng dụng AI có khả năng mở rộng và phục hồi cao. Step Functions xử lý quản lý trạng thái phức tạp, trong khi SQS/SNS giúp tách rời các thành phần. Kết hợp với AI Services tạo nên hệ thống phản ứng nhanh, thông minh.