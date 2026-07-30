---
title: "Proposal"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
includeInReport: false
---

Trong phần này, nhóm chúng tôi tóm tắt nội dung dự án mà chúng tôi **dự kiến** thực hiện trong kỳ thực tập First Cloud AI Journey (FCAJ).

# Hệ thống Cảnh báo sớm Kết quả Học tập của Học sinh/Sinh viên
## Giải pháp AWS Serverless trong việc Dự đoán và Cảnh báo Rủi ro Học tập

### 1. Tóm tắt Dự án

**Hệ thống Cảnh báo sớm Kết quả Học tập (SP-EWS)** là một Hệ thống Thông tin cloud-native được xây dựng nhằm giúp giảng viên và cán bộ quản lý đào tạo phát hiện những học sinh/sinh viên có rủi ro đạt kết quả học tập kém **trước khi** quá muộn để can thiệp. Hệ thống tiếp nhận dữ liệu học tập và hành vi của khoảng 3.000 học sinh/sinh viên, dự đoán những ai đang gặp rủi ro bằng mô hình Machine Learning, và hiển thị kết quả thông qua một dashboard dạng Hệ thống Hỗ trợ Ra quyết định (DSS) kết hợp với các cảnh báo email tự động cho những học sinh/sinh viên có rủi ro cao.

Nền tảng được xây dựng hoàn toàn trên các dịch vụ serverless và managed services của AWS — Amazon S3, AWS Lambda, Amazon DynamoDB, Amazon API Gateway, Amazon SageMaker (Serverless Inference), Amazon CloudFront, Amazon SNS, và Amazon CloudWatch — tuân thủ theo AWS Well-Architected Framework. Vì mọi tầng đều là serverless (bao gồm cả SageMaker Serverless Inference chỉ tính phí theo mỗi yêu cầu), chi phí vận hành ở mức tối thiểu và không phát sinh chi phí duy trì tài nguyên khi rảnh rỗi.

### 2. Mô tả Bối cảnh & Tuyên bố Bài toán

#### Vấn đề là gì?

Tại nhiều trường học và trung tâm đào tạo, việc theo dõi kết quả học tập của học sinh/sinh viên vẫn được thực hiện thủ công qua các bảng tính và hệ thống rời rạc. Khi quy mô lớp học tăng lên, giảng viên phát hiện ra những học sinh/sinh viên gặp khó khăn quá muộn, và việc can thiệp học tập thường diễn ra sau khi nó không còn mang lại hiệu quả. Hiện chưa có một hệ thống tập trung nào giúp hợp nhất dữ liệu học sinh/sinh viên, tự động gắn cờ những trường hợp có rủi ro, hoặc cung cấp góc nhìn tổng quan nhanh chóng cho việc ra quyết định.

#### Giải pháp

SP-EWS cung cấp một quy trình tự động hóa và tập trung:

- Bộ dữ liệu CSV được tải lên **Amazon S3**, kích hoạt một hàm **AWS Lambda** làm nhiệm vụ tiếp nhận để ghi các bản ghi vào **Amazon DynamoDB**.
- Một Lambda dự đoán theo đợt (batch-prediction) gọi một endpoint **Amazon SageMaker Serverless Inference** (XGBoost) để tính toán xác suất rủi ro cho mỗi học sinh/sinh viên và lưu kết quả vào DynamoDB.
- Một REST API trên **Amazon API Gateway** cung cấp dữ liệu, và một dashboard **React** được lưu trữ trên **Amazon S3 + CloudFront** giúp trực quan hóa các chỉ số KPI, sự phân bố rủi ro, và danh sách các học sinh/sinh viên có rủi ro cao.
- **Amazon SNS** gửi cảnh báo qua email cho những học sinh/sinh viên có rủi ro cao, và **Amazon CloudWatch** cung cấp log, metric cũng như các alarm.

Giảng viên cũng có thể thêm, sửa, xóa các bản ghi học sinh/sinh viên và chạy dự đoán theo yêu cầu (on-demand) cho một học sinh/sinh viên duy nhất mà không cần lưu lại.

#### Lợi ích và Tỷ suất Hoàn vốn (ROI)

Hệ thống thay thế việc đánh giá thủ công bằng một quy trình cảnh báo sớm tự động, cho phép can thiệp học tập kịp thời. Hệ thống giúp tập trung hóa dữ liệu học sinh/sinh viên, nâng cao độ tin cậy của dữ liệu, và cung cấp một nền tảng dữ liệu & ML có thể tái sử dụng cho các dự án phân tích dữ liệu học tập trong tương lai. Vì kiến trúc hoàn toàn là serverless và sử dụng SageMaker Serverless Inference (trả phí theo yêu cầu, không tốn chi phí duy trì máy chủ 24/7), chi phí vận hành vẫn nằm trong phạm vi AWS Free Tier đối với quy mô khối lượng công việc và tần suất sử dụng này. Lợi ích chính thu được là tiết kiệm thời gian cho giảng viên và phát hiện sớm hơn những học sinh/sinh viên gặp rủi ro.

### 3. Kiến trúc Giải pháp

Nền tảng sử dụng kiến trúc serverless toàn diện (end-to-end). Dữ liệu chảy từ bước tải lên file CSV thông qua các khâu xử lý, dự đoán, lưu trữ, API, và được hiển thị trên dashboard React phân phối qua CloudFront:

```
CSV Dataset
    ↓
Amazon S3 (raw-data / predict-input / model)
    ↓
AWS Lambda (ingest + batch predict)
    ↓
Amazon DynamoDB (student_records + prediction_results)
    ↓
Amazon API Gateway (REST)
    ↓
React Dashboard (Amazon S3 + CloudFront)

Amazon SageMaker Serverless Inference (XGBoost)  →  Xác suất rủi ro
Amazon SNS                                       →  Cảnh báo rủi ro cao qua email
Amazon CloudWatch                                →  Logs, metrics, alarms
```

{{< figure src="/fcj-workshop-template/images/5-Workshop/5.1-Workshop-overview/Solution_Archi.jpg" width="800" >}}

#### Các dịch vụ AWS được sử dụng

- **Amazon S3**: Lưu trữ bộ dữ liệu, đầu vào dự đoán, các file artifact của mô hình, và bản build frontend.
- **AWS Lambda**: Xử lý luồng tiếp nhận dữ liệu, dự đoán theo đợt, dự đoán theo yêu cầu, và logic CRUD.
- **Amazon DynamoDB**: Lưu trữ `student_records` và `prediction_results` (chế độ dung lượng on-demand).
- **Amazon API Gateway**: Cung cấp REST API cho dashboard truy xuất.
- **Amazon SageMaker (Serverless Inference)**: Phục vụ mô hình dự đoán rủi ro XGBoost đã huấn luyện, tính phí theo từng yêu cầu.
- **Amazon CloudFront**: Phân phối dashboard React qua giao thức HTTPS có tích hợp bộ nhớ đệm (caching).
- **Amazon SNS**: Gửi cảnh báo email cho các trường hợp học sinh/sinh viên có rủi ro cao.
- **Amazon CloudWatch**: Cung cấp log, metric và các alarm.
- **AWS IAM**: Áp dụng quyền tối thiểu (least-privilege) cho từng hàm Lambda.

#### Thiết kế các Thành phần

- **Data Ingestion (Tiếp nhận Dữ liệu)**: Việc tải file lên prefix `raw-data/` sẽ kích hoạt một Lambda để phân tích file CSV và ghi các bản ghi vào `student_records`.
- **Machine Learning**: Một Lambda dự đoán theo đợt (được kích hoạt bởi `predict-input/`) gọi SageMaker endpoint theo từng đợt, ghi xác suất rủi ro vào `prediction_results`. Một endpoint theo yêu cầu thực hiện dự đoán cho một học sinh/sinh viên duy nhất mà không lưu lại.
- **Data Storage (Lưu trữ Dữ liệu)**: DynamoDB lưu giữ các bản ghi học sinh/sinh viên và kết quả dự đoán; S3 lưu trữ các bộ dữ liệu và file artifact của mô hình.
- **API Layer (Tầng API)**: API Gateway kết hợp tích hợp Lambda proxy cung cấp các endpoint đọc dữ liệu, dự đoán và thao tác CRUD.
- **Web Interface (Giao diện Web)**: Một dashboard React trên S3 + CloudFront hiển thị các KPI, phân bố rủi ro, bảng danh sách rủi ro cao, và các trang CRUD/dự đoán.
- **Alerts & Monitoring (Cảnh báo & Giám sát)**: SNS gửi bản tóm tắt rủi ro cao qua email; CloudWatch alarms thông báo khi có lỗi Lambda và phản hồi API 5XX.

### 4. Triển khai Kỹ thuật

**Các Giai đoạn Triển khai**

Dự án trải qua bốn giai đoạn trong suốt kỳ thực tập:

- **Thiết kế & Kiến trúc**: Nghiên cứu bộ dữ liệu, xác định mục tiêu ML (`at_risk`), và thiết kế kiến trúc serverless tuân theo Well-Architected Framework.
- **Core Backend & Data Pipeline**: Xây dựng luồng tiếp nhận S3 → Lambda → DynamoDB và read API với API Gateway.
- **Frontend & Tích hợp ML**: Xây dựng và triển khai dashboard React lên S3 + CloudFront, triển khai SageMaker Serverless endpoint, kết nối tính năng dự đoán theo đợt và theo yêu cầu cùng các API CRUD.
- **Giám sát, Củng cố Báo mật & Dọn dẹp**: Thêm cảnh báo SNS và CloudWatch alarms, áp dụng các cải tiến Well-Architected (quyền tối thiểu IAM, siết chặt CORS, S3 lifecycle, DLQ), thực hiện kiểm thử lỗi (failure testing), và viết tài liệu quy trình dọn dẹp chi tiết.

**Yêu cầu Kỹ thuật**

- **Bộ dữ liệu**: Khoảng 3.000 bản ghi học sinh/sinh viên với năm đặc trưng số cốt lõi (`attendance_rate`, `assignment_avg_score`, `exam_avg_score`, `homework_submission_rate`, `class_participation`) và một nhãn nhị phân `at_risk`. Thứ tự đặc trưng phải khớp với định dạng huấn luyện mô hình đối với CSV endpoint.
- **Mô hình**: Bộ phân loại nhị phân XGBoost được triển khai dưới dạng một SageMaker Serverless Inference endpoint (bộ nhớ 1 GB, độ song song tối đa / max concurrency là 5).
- **Backend**: Các hàm Lambda viết bằng Python 3.12. Hàm tiếp nhận dữ liệu được đóng gói dạng file ZIP cùng với `pandas`; các hàm CRUD và dự đoán theo yêu cầu chỉ sử dụng `boto3`. Tích hợp Lambda proxy yêu cầu mã nguồn Lambda phải trả về đầy đủ các header CORS.
- **Frontend**: React (Vite) sử dụng axios và recharts, được triển khai lên S3 static hosting và phân phối qua CloudFront với cơ chế điều hướng SPA (403/404 → `index.html`).
- **Region**: Tất cả tài nguyên được khởi tạo tại khu vực **Châu Á - Thái Bình Dương (Singapore) `ap-southeast-1`** để tránh các lỗi liên khu vực (cross-region).

### 5. Lộ trình & Các Cột mốc Quan trọng

Kỳ thực tập kéo dài trong **12 tuần**, mỗi tuần đều tạo ra một phần sản phẩm tăng tiến có thể hoạt động và kiểm thử được:

- **Tuần 1–2**: Tìm hiểu nền tảng AWS, các dịch vụ cốt lõi và xác định phạm vi dự án.
- **Tuần 3–4**: Thiết kế kiến trúc, xây dựng backend data pipeline (S3, DynamoDB, ingestion Lambda), và Students API.
- **Tuần 5**: Xây dựng dashboard React và triển khai lên CloudFront.
- **Tuần 6–8**: Huấn luyện ML, triển khai SageMaker endpoint, thực hiện dự đoán theo đợt, xây dựng API dự đoán theo yêu cầu + các API CRUD cùng cảnh báo SNS.
- **Tuần 9–10**: Nâng cấp DSS dashboard và thiết lập hệ thống giám sát/alarms trên CloudWatch.
- **Tuần 11–12**: Kiểm thử, đánh giá bảo mật, tối ưu hóa chi phí, hoàn thiện tài liệu song ngữ, dọn dẹp tài nguyên và thực hiện buổi workshop cuối kỳ.

### 6. Ước tính Chi phí

Vì kiến trúc hoàn toàn là serverless và SageMaker sử dụng Serverless Inference (tính phí theo yêu cầu, không tốn chi phí duy trì máy chủ khi rảnh rỗi), chi phí ước tính hàng tháng là rất nhỏ và phần lớn nằm trong phạm vi AWS Free Tier cho khối lượng công việc này.

#### Chi phí Hạ tầng Ước tính

- **AWS Lambda**: ~$0.00/tháng (lượng gọi hàm thấp, nằm trong Free Tier).
- **Amazon DynamoDB (on-demand)**: ~$0.00–$0.10/tháng cho ~3.000 bản ghi và lượng đọc/ghi nhẹ.
- **Amazon S3**: ~$0.05/tháng (bộ dữ liệu, file artifact của mô hình, tài nguyên frontend).
- **Amazon API Gateway**: ~$0.01/tháng (lượng yêu cầu thấp).
- **Amazon CloudFront**: ~$0.00/tháng (nằm trong Free Tier cho lưu lượng thử nghiệm/demo).
- **Amazon SageMaker Serverless Inference**: chỉ tính phí theo từng yêu cầu (thời gian tính toán + số lượng yêu cầu); không tốn phí khi rảnh rỗi.
- **Amazon SNS / CloudWatch**: ~$0.00/tháng (nằm trong Free Tier).

### 7. Đánh giá Rủi ro

#### Ma trận Rủi ro

- **Thiếu xác thực trên API**: Tác động cao, khả năng xảy ra trung bình. Các endpoint trên API Gateway (bao gồm cả DELETE) hiện chưa có cơ chế xác thực.
- **Quyền IAM quá rộng**: Tác động trung bình, khả năng xảy ra trung bình. Một số role đang sử dụng các policy quản lý FullAccess thay vì phân quyền tối thiểu.
- **Nghẽn độ song song (concurrency throttling) trên SageMaker**: Tác động thấp, khả năng xảy ra thấp. Độ song song tối đa là 5; các lệnh gọi theo đợt song song có thể gặp lỗi HTTP 429.
- **Vượt ngân sách**: Tác động thấp, khả năng xảy ra thấp. Việc sử dụng dịch vụ Serverless nằm trong phạm vi Free Tier cho khối lượng công việc này.

#### Chiến lược Giảm thiểu Rủi ro

- **Xác thực**: Bổ sung tối thiểu API Key + Usage Plan, và nâng cấp lên Amazon Cognito để xác thực người dùng thực tế.
- **IAM**: Thay thế các policy FullAccess bằng các inline policy phân quyền tối thiểu, giới hạn chính xác các hành động và ARN tài nguyên.
- **Xử lý song song**: Gọi SageMaker endpoint theo các đợt tuần tự (ví dụ: 6 đợt, mỗi đợt 500 bản ghi cho tổng số 3.000 bản ghi) thay vì gọi song song.
- **CORS & Tính khả dụng**: Giới hạn CORS chỉ cho tên miền CloudFront, thêm SQS Dead Letter Queue cho Lambda dự đoán theo đợt bất đồng bộ, và áp dụng các chính sách S3 lifecycle.

### 8. Kết quả Dự kiến

#### Những Cải tiến Kỹ thuật

Hệ thống cảnh báo sớm tự động dựa trên ML sẽ thay thế việc đánh giá thủ công học sinh/sinh viên. Giảng viên sở hữu một DSS dashboard thời gian thực, khả năng dự đoán rủi ro theo yêu cầu, và các cảnh báo tự động qua email đối với những trường hợp rủi ro cao.

#### Giá trị Lâu dài

Dự án mang lại một nền tảng serverless và Machine Learning có thể tái sử dụng cho các bài toán phân tích dữ liệu học tập, một tài liệu workshop song ngữ (Anh/Việt) ghi lại toàn bộ quá trình xây dựng, cùng bài đánh giá Well-Architected giúp chỉ ra các cải tiến cụ thể để sẵn sàng đưa vào môi trường thực tế (sản xuất) như xác thực, phân quyền tối thiểu IAM, IaC, DLQ cho các phiên bản tiếp theo.
