---
title: "Week 4 Worklog"
date: 2026-06-22
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu Tuần 4:

* Khám phá các AWS AI Services cho phân tích ảnh, văn bản và giọng nói.
* Tích hợp Rekognition, Comprehend, Translate và Polly vào ứng dụng.
* Xây dựng ứng dụng AI đa phương thức.
* Hiểu về bảo mật và quản trị cho các AI Services.

### Nhiệm vụ thực hiện trong tuần:

| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | ---- | ---------- | --------------- | ------------------ |
| 1 | **Amazon Rekognition:** <br>&emsp; + Phân tích ảnh và video <br>&emsp; + Phát hiện, so sánh và tìm kiếm khuôn mặt <br>&emsp; + Custom Labels (huấn luyện model tùy chỉnh) | 22/06/2026 | 22/06/2026 | Rekognition Docs |
| 2 | **Amazon Comprehend:** <br>&emsp; + Xử lý ngôn ngữ tự nhiên (NLP) <br>&emsp; + Nhận diện thực thể, cụm từ khóa, phân tích cảm xúc <br>&emsp; + Custom Classification và Custom Entity Recognition | 23/06/2026 | 23/06/2026 | Comprehend Docs |
| 3 | **Amazon Translate & Polly:** <br>&emsp; + Dịch ngôn ngữ với Translate <br>&emsp; + Chuyển văn bản thành giọng nói với Polly (neural voice) <br>&emsp; + Use case cho đa ngôn ngữ và tiếp cận (accessibility) | 24/06/2026 | 24/06/2026 | Translate & Polly |
| 4 | **Workshop tích hợp AWS AI Services:** <br>&emsp; + Xây dựng ứng dụng serverless kết hợp Rekognition, Comprehend, Translate <br>&emsp; + Xử lý ảnh và văn bản trong một pipeline | 25/06/2026 | 25/06/2026 | AI Services Workshop |
| 5 | **Bảo mật và Quản trị:** <br>&emsp; + IAM policy cho AI Services <br>&emsp; + AWS Firewall Manager và GuardDuty <br>&emsp; + Mã hóa và bảo vệ dữ liệu (KMS) | 26/06/2026 | 26/06/2026 | Security Modules |
| 6 | **SageMaker kết hợp AI Services:** <br>&emsp; + Kết hợp built‑in algorithm với AI Services cho giải pháp lai ghép <br>&emsp; + Giải thích model với SageMaker Clarify | 27/06/2026 | 27/06/2026 | SageMaker Clarify |

### Thành tựu đạt được Tuần 4:

#### Amazon Rekognition
* Nhận diện đối tượng, cảnh vật và khuôn mặt trong ảnh/video.
* So sánh và đối chiếu khuôn mặt với một collection.
* Tạo custom label model để phát hiện đối tượng đặc thù (ví dụ: lỗi sản phẩm).
* Sử dụng Rekognition Video để phân tích luồng sự kiện theo thời gian thực.

#### Amazon Comprehend
* Trích xuất thực thể, cụm từ then chốt và cảm xúc từ văn bản.
* Xây dựng custom classifier cho danh mục sản phẩm.
* Tạo custom entity recognizer cho thuật ngữ chuyên ngành.
* Tích hợp với S3 và Lambda để tự động phân tích văn bản.

#### Amazon Translate và Polly
* Dịch nội dung đa ngôn ngữ bằng Translate.
* Tạo giọng nói tự nhiên với Polly (neural voices).
* Sử dụng SSML để điều khiển phát âm và ngữ điệu.
* Xây dựng prototype hỗ trợ chat đa ngôn ngữ.

#### Bảo mật & Quản trị
* Áp dụng IAM policy chi tiết cho AI Services.
* Bật CloudTrail và GuardDuty để phát hiện mối đe dọa.
* Mã hóa dữ liệu lưu trữ với KMS cho S3 và DynamoDB.
* Thiết lập AWS Firewall Manager để bảo vệ API Gateway.

### Bài học kinh nghiệm chính:

> **Điểm nhấn:** AWS AI Services cung cấp các khả năng trí tuệ nhân tạo sẵn sàng sử dụng, giúp giảm rào cản khi tích hợp AI vào ứng dụng. Kết hợp với các best practice về bảo mật, chúng tạo nền tảng vững chắc cho các hệ thống sản xuất.