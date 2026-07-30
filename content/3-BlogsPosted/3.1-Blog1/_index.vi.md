---
title: "Deploy XGBoost Serverless trên AWS SageMaker: Hành trình từ Lambda đến SageMaker Serverless"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Giới thiệu

Trong quá trình thực tập, mình tham gia phát triển một hệ thống cảnh báo sớm sinh viên có nguy cơ học tập thấp. Một trong những thành phần quan trọng của hệ thống là mô hình XGBoost dùng để dự đoán xác suất sinh viên có nguy cơ học lực kém dựa trên dữ liệu học tập và rèn luyện.

Sau khi hoàn thành việc huấn luyện mô hình, bài toán tiếp theo là làm thế nào để triển khai mô hình thành một API để website có thể gửi dữ liệu và nhận kết quả dự đoán theo thời gian thực.

## Bài toán đặt ra

Yêu cầu của project khá rõ ràng:

- Có API để frontend hoặc backend gọi dự đoán.
- Chi phí thấp vì đây là project thực tập.
- Không phải duy trì một EC2 chạy 24/7.
- Có thể mở rộng khi có nhiều request nhưng gần như không tốn chi phí khi không sử dụng.

Ban đầu, mình nghĩ ngay đến AWS Lambda vì đây là dịch vụ serverless quen thuộc và chỉ tính phí theo số lần thực thi.

## Thử deploy bằng AWS Lambda

Ý tưởng ban đầu khá đơn giản:

- Đóng gói model XGBoost.
- Đưa các thư viện như xgboost, numpy, joblib vào Lambda Layer.
- Lambda nhận request, load model và trả về kết quả dự đoán.

Tuy nhiên, khi bắt đầu đóng gói, mình gặp ngay một vấn đề khá phổ biến với các ứng dụng Machine Learning:

Tổng dung lượng của Lambda Layer vượt quá giới hạn 250 MB sau khi giải nén.

Các thư viện phục vụ Machine Learning như XGBoost, NumPy, SciPy có kích thước khá lớn. Mặc dù có nhiều cách tối ưu hoặc sử dụng container image cho Lambda, nhưng chúng đều làm cho quá trình triển khai trở nên phức tạp hơn so với yêu cầu của project.

Lúc này mình nhận ra rằng Lambda không phải là lựa chọn phù hợp cho trường hợp này.

## Vì sao mình chuyển sang SageMaker Serverless?

Sau khi tìm hiểu các dịch vụ của AWS dành cho Machine Learning, mình quyết định sử dụng AWS SageMaker Serverless Inference.

Điểm khiến mình lựa chọn dịch vụ này là:

- Không cần quản lý server.
- Không phải tự xây dựng môi trường chạy XGBoost.
- AWS đã cung cấp sẵn container phục vụ inference cho XGBoost.
- Endpoint tự động scale theo lượng request.
- Khi không có request, endpoint có thể scale về 0 nên không phải duy trì tài nguyên chạy liên tục.

Điều này giúp mình tập trung vào mô hình thay vì xử lý các vấn đề về hạ tầng.

## Quá trình triển khai

### 1. Chuẩn hóa mô hình

Trong quá trình huấn luyện, mình lưu model bằng Python để thuận tiện cho việc thử nghiệm. Tuy nhiên, khi triển khai trên SageMaker, mình chuyển model sang định dạng native của XGBoost bằng Booster.save_model() để đảm bảo container XGBoost của SageMaker có thể load trực tiếp mà không phụ thuộc vào môi trường Python khi train. Điều này cũng giúp việc deploy ổn định hơn.

### 2. Chuẩn bị package deploy

Sau khi có model, mình đóng gói các thành phần cần thiết để SageMaker phục vụ inference, bao gồm:

- File model.
- File xử lý dữ liệu đầu vào.
- Logic chuyển đổi request sang định dạng mà XGBoost có thể dự đoán.
- Logic xử lý kết quả đầu ra.

Package sau đó được upload lên Amazon S3 để SageMaker sử dụng trong quá trình tạo Endpoint.

### 3. Xây dựng logic inference

Mình xây dựng một file inference.py để SageMaker biết cách xử lý request. File này thực hiện các bước:

- Nhận dữ liệu JSON từ backend.
- Chuyển dữ liệu thành định dạng mà XGBoost yêu cầu.
- Thực hiện prediction.
- Trả về xác suất dự đoán dưới dạng JSON.

Nhờ vậy backend chỉ cần gửi dữ liệu và nhận kết quả mà không cần quan tâm tới cách mô hình hoạt động bên trong.

### 4. Deploy Serverless Endpoint

Sau khi chuẩn bị xong model và mã inference, mình tạo SageMaker Serverless Endpoint với cấu hình:

- Memory: 1024 MB
- Endpoint mode: Serverless

Sau khi endpoint được tạo thành công, backend chỉ cần gọi API của SageMaker mỗi khi cần dự đoán. AWS sẽ tự động cấp phát tài nguyên khi có request và giải phóng tài nguyên khi không còn lưu lượng truy cập.

## Kết quả

Sau khi chuyển sang SageMaker Serverless:

- Không còn gặp giới hạn dung lượng như Lambda Layer.
- Không cần tự xây dựng môi trường chạy XGBoost.
- Endpoint hoạt động ổn định và có thể phục vụ prediction theo thời gian thực.
- Không cần duy trì một máy chủ chạy liên tục, phù hợp với quy mô của project thực tập.