---
title: "Các bài Blog đã đăng"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

### [Blog 1 - Deploy XGBoost Serverless trên AWS SageMaker](3.1-Blog1/)

Bài blog chia sẻ hành trình triển khai mô hình XGBoost từ AWS Lambda sang SageMaker Serverless Inference. Ban đầu, tác giả thử deploy bằng Lambda nhưng gặp giới hạn dung lượng layer 250 MB do các thư viện ML lớn (XGBoost, NumPy, SciPy). Sau khi nhận ra Lambda không phù hợp cho trường hợp này, tác giả chuyển sang SageMaker Serverless Inference—một dịch vụ fully managed tự động scale theo số lượng request và scale về 0 khi không sử dụng. Blog bao gồm quy trình triển khai: chuẩn hóa mô hình sang định dạng native XGBoost, chuẩn bị inference package, xây dựng logic inference và cấu hình serverless endpoint. Kết quả là một giải pháp tiết kiệm chi phí, có thể mở rộng và không cần quản lý hạ tầng.

### [Blog 2 - Xây dựng hệ thống Batch Prediction tự động với Amazon S3, AWS Lambda và SageMaker](3.2-Blog2/)
**Trạng thái:** ⏳ *Chờ Admin duyệt*  

Bài blog trình bày cách xây dựng pipeline batch prediction theo kiến trúc event-driven cho các trường hợp cần đánh giá hàng trăm sinh viên cùng lúc thay vì dự đoán real-time từng người một. Hệ thống cho phép giảng viên chỉ cần upload file CSV lên Amazon S3, tự động kích hoạt Lambda. Lambda đọc file, tiền xử lý dữ liệu, gọi SageMaker Serverless Endpoint cho từng sinh viên, phân loại sinh viên có nguy cơ cao dựa trên ngưỡng đã xác định và gửi báo cáo tổng hợp qua email. Blog cũng đề cập đến các thách thức gặp phải như cấu hình timeout Lambda và IAM permissions, cùng cách giải quyết.

### [Blog 3 - Tự động gửi email cảnh báo với AWS SNS](3.3-Blog3/)
**Trạng thái:** ⏳ *Chờ Admin duyệt*  

Bài blog giới thiệu cách tích hợp AWS SNS (Simple Notification Service) vào hệ thống batch prediction để tự động gửi email cảnh báo cho giảng viên khi phát hiện sinh viên có nguy cơ cao. SNS là dịch vụ pub/sub messaging của AWS cho phép gửi thông báo đến nhiều subscriber qua email, SMS hoặc HTTP endpoints. Blog trình bày từng bước triển khai: tạo SNS Topic, cấu hình email subscription (bao gồm bước xác nhận), cấu hình IAM permissions cho Lambda để publish message và tích hợp SNS vào workflow. Một lỗi phổ biến—quên xác nhận email subscription—cũng được đề cập kèm giải pháp thực tế.