---
title: "Hàm Lambda Dự Báo Theo Đợt"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 5.5.2. </b> "
---

Tạo hàm `predictRiskFunction`. Hàm này đọc dữ liệu CSV, gọi SageMaker endpoint theo các đợt (batches), ghi kết quả vào bảng `prediction_results` và gửi thông tin tổng hợp các sinh viên có nguy cơ cao qua dịch vụ SNS.

#### Các điểm lưu ý quan trọng trong thiết kế

- **Thứ tự các đặc trưng (Features)** phải khớp chính xác tuyệt đối với quá trình huấn luyện.
- Gọi endpoint theo **từng đợt (batches)** (ví dụ: 500 dòng một lần) thay vì gọi từng dòng một, nhằm tránh lỗi vượt quá thời gian chờ (timeout) khi xử lý ~3.000 bản ghi.
- Ghi kết quả vào DynamoDB bằng phương thức `batch_writer()`.
- Chỉ gửi cảnh báo SNS khi có sinh viên thuộc nhóm nguy cơ cao.

#### Biến môi trường (Environment variables)

```text
SAGEMAKER_ENDPOINT = <tên-endpoint>
PREDICTION_TABLE   = prediction_results
THRESHOLD          = 0.5
SNS_TOPIC_ARN      = <arn-cua-topic>   # không bắt buộc
BATCH_SIZE         = 500
```

#### Quyền IAM (IAM permissions)

Role thực thi cần được cấp các quyền sau (thu hẹp theo nguyên tắc quyền tối thiểu nếu có thể):

- `sagemaker:InvokeEndpoint`
- `dynamodb:BatchWriteItem` / `PutItem` trên bảng `prediction_results`
- `sns:Publish` trên topic cảnh báo

{{% notice info %}}
Nếu bạn gặp lỗi `AccessDeniedException` đối với thao tác `BatchWriteItem`, nguyên nhân là role thực thi đang thiếu quyền ghi vào DynamoDB. Nếu gặp lỗi `ResourceNotFoundException`, bảng `prediction_results` không tồn tại hoặc được tạo ở một region khác.
{{% /notice %}}

#### Kiểm thử

Tải lên một tệp CSV nhỏ, sau đó xác nhận:

- CloudWatch hiển thị nhật ký: `Saved N predictions to prediction_results`.
- Bảng `prediction_results` trong DynamoDB chứa các đối tượng có thuộc tính `prediction` và `probability`.
- Nhận được email cảnh báo từ SNS nếu phát hiện sinh viên có nguy cơ cao.

![Prediction results in DynamoDB]( /images/5-Workshop/5.5-ML/prediction-results.png)