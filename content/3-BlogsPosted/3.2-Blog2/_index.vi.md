---
title: "Xây dựng hệ thống Batch Prediction tự động với Amazon S3, AWS Lambda và SageMaker"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---


## Giới thiệu

Ở bài viết trước, mình đã chia sẻ cách deploy mô hình XGBoost lên AWS SageMaker Serverless để phục vụ dự đoán theo thời gian thực (real-time inference). Giải pháp này hoạt động tốt khi hệ thống cần dự đoán cho từng sinh viên ngay trên dashboard.

Tuy nhiên, trong quá trình làm việc với giảng viên, mình nhận ra một nhu cầu khác:

Giảng viên thường muốn đánh giá toàn bộ một lớp học hoặc hàng trăm sinh viên cùng lúc thay vì nhập từng sinh viên để dự đoán.

Nếu tiếp tục sử dụng API real-time, backend sẽ phải gửi hàng trăm request liên tiếp đến SageMaker, vừa mất thời gian vừa không thuận tiện cho người sử dụng.

Vì vậy, mình quyết định xây dựng một pipeline batch prediction theo hướng event-driven, nơi giảng viên chỉ cần upload một file CSV và toàn bộ quá trình xử lý sẽ diễn ra tự động.

## Bài toán đặt ra

Mục tiêu của hệ thống là:

- Giảng viên chỉ cần upload một file CSV chứa danh sách sinh viên.
- Hệ thống tự động đọc dữ liệu và thực hiện dự đoán cho từng sinh viên.
- Tổng hợp danh sách những sinh viên có nguy cơ học tập cao.
- Gửi kết quả qua email sau khi xử lý hoàn tất.
- Không cần chạy server liên tục để tiết kiệm chi phí.

## Vì sao mình chọn AWS Lambda?

Sau khi đã có SageMaker Serverless Endpoint từ bài trước, mình cần một dịch vụ có thể:

- Tự động chạy khi có file mới.
- Đọc dữ liệu từ Amazon S3.
- Gọi SageMaker để dự đoán.
- Xử lý kết quả.
- Gửi email thông báo.

AWS Lambda đáp ứng rất tốt các yêu cầu này.

Điểm mình thích nhất là Lambda hoạt động theo cơ chế event-driven. Thay vì backend phải liên tục kiểm tra xem có file mới hay chưa, Lambda chỉ được kích hoạt khi Amazon S3 phát sinh sự kiện upload. Điều này giúp giảm đáng kể lượng tài nguyên phải duy trì và giữ cho kiến trúc đơn giản hơn.

## Khó khăn gặp phải

Trong quá trình triển khai, mình gặp hai vấn đề chính.

### 1. Timeout của Lambda

Thời gian timeout mặc định của Lambda chỉ khoảng 3 giây. Trong khi đó, một file CSV có thể chứa hàng trăm sinh viên và Lambda cần: đọc file, xử lý dữ liệu, gọi SageMaker nhiều lần, tổng hợp kết quả, gửi email. Tổng thời gian xử lý có thể kéo dài hơn nhiều so với cấu hình mặc định.

Giải pháp của mình là tăng thời gian timeout của Lambda lên 5 phút, đủ để xử lý các file có kích thước phù hợp với quy mô của project.

### 2. Cấu hình IAM Permissions

Lambda cần tương tác với nhiều dịch vụ AWS khác nhau nên phải được cấp đúng quyền.

IAM Role của Lambda được cấu hình để:

- Đọc file từ Amazon S3.
- Invoke SageMaker Endpoint.
- Gửi email thông qua Amazon SNS.
- Ghi log lên Amazon CloudWatch để theo dõi quá trình xử lý.

Nếu thiếu bất kỳ quyền nào, toàn bộ pipeline sẽ dừng ngay tại bước tương ứng.

## Mình đã triển khai như thế nào?

### 1. Trigger Lambda khi có file mới

Đầu tiên, mình cấu hình Amazon S3 Event Notification để mỗi khi một file CSV mới được upload vào bucket, Lambda sẽ tự động được kích hoạt. Nhờ vậy, người dùng không cần nhấn nút "Chạy dự đoán" hay gọi thêm API nào khác.

### 2. Đọc dữ liệu từ file CSV

Sau khi được kích hoạt, Lambda lấy thông tin bucket và tên file từ sự kiện S3. Lambda đọc nội dung CSV và chuyển từng dòng dữ liệu thành thông tin của một sinh viên. Trong bước này, mình cũng kiểm tra dữ liệu đầu vào để tránh các trường hợp thiếu cột hoặc sai định dạng.

### 3. Chuẩn bị dữ liệu cho mô hình

Model XGBoost yêu cầu dữ liệu đầu vào phải có đúng thứ tự và đúng số lượng đặc trưng giống với quá trình huấn luyện. Vì vậy, Lambda thực hiện các bước tiền xử lý cần thiết trước khi gửi dữ liệu sang SageMaker. Việc giữ thống nhất quy trình xử lý giữa training và inference giúp hạn chế sai lệch trong kết quả dự đoán.

### 4. Gọi SageMaker Serverless Endpoint

Với mỗi sinh viên, Lambda gửi request đến SageMaker Endpoint thông qua API InvokeEndpoint. Model XGBoost sẽ trả về xác suất sinh viên thuộc nhóm có nguy cơ học tập thấp. Lambda tiếp tục xử lý kết quả này để phục vụ bước phân loại.

### 5. Phân loại sinh viên có nguy cơ

Sau khi nhận xác suất dự đoán, Lambda so sánh với ngưỡng rủi ro đã được xác định trong quá trình đánh giá mô hình. Những sinh viên vượt ngưỡng sẽ được đưa vào danh sách cần theo dõi. Cuối quá trình xử lý, Lambda tạo báo cáo tổng hợp bao gồm: Tổng số sinh viên được phân tích, số sinh viên có nguy cơ học tập cao, danh sách sinh viên cần được quan tâm.

## Kết quả đạt được

- Xây dựng thành công pipeline batch prediction tự động theo kiến trúc event-driven.
- Tự động kích hoạt xử lý khi có file CSV mới được tải lên Amazon S3.
- Thực hiện dự đoán cho toàn bộ danh sách sinh viên bằng SageMaker Serverless Endpoint.
- Tự động tổng hợp danh sách sinh viên có nguy cơ học tập cao.
- Gửi kết quả qua email sau khi quá trình xử lý hoàn tất.
- Giảm thao tác thủ công, tiết kiệm chi phí vận hành và dễ dàng mở rộng hệ thống.