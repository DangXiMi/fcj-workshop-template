---
title: "Tự động gửi email cảnh báo với AWS SNS"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

## Giới thiệu

Một yêu cầu quan trọng của dự án là phải gửi cảnh báo ngay cho giảng viên khi sinh viên bị dự đoán là "High Risk". Thay vì phải kiểm tra database thủ công, mình dùng AWS SNS để gửi email real-time. Trong hệ thống batch prediction, SNS được sử dụng để gửi email tổng hợp sau khi xử lý xong toàn bộ file CSV.

## Amazon SNS là gì?

SNS là dịch vụ pub/sub messaging của AWS. Nó cho phép bạn gửi thông báo đến nhiều subscriber (email, SMS, HTTP endpoints, hoặc các AWS services khác) một cách tức thời. Mình dùng SNS với giao thức Email để gửi cảnh báo đến giảng viên.

## Vì sao mình chọn nó?

Mình cần một cách đơn giản và đáng tin cậy để gửi email mà không cần phải tự xây dựng hệ thống gửi mail. SNS cung cấp sẵn tính năng này, tích hợp dễ dàng với Lambda, và có free tier 1.000 email mỗi tháng.

## Vấn đề phát sinh

Mình tạo topic và subscription thành công, nhưng không nhận được email nào. Kiểm tra trên console thì thấy status "Pending confirmation".

## Cách giải quyết

SNS yêu cầu xác nhận qua email trước khi gửi thông báo. Mình đã quên click vào link xác nhận trong hộp thư. Sau khi xác nhận, mọi thứ chạy ngon lành.

## Mình đã làm như thế nào?

### Tạo kênh thông báo với SNS

Mình tạo một SNS Topic để làm nơi trung gian nhận các thông báo từ hệ thống. Topic này chịu trách nhiệm phân phối cảnh báo đến các subscriber đã đăng ký.

### Kết nối người nhận thông báo

Mình cấu hình email subscription cho giảng viên. Sau khi đăng ký, email cần được xác nhận trước khi SNS có thể gửi thông báo.

### Cấp quyền cho Lambda gửi thông báo

Mình cấu hình quyền IAM để Lambda có thể publish message lên SNS Topic sau khi hoàn thành quá trình dự đoán.

### Tích hợp SNS vào workflow

Sau khi Lambda xử lý xong dữ liệu và xác định danh sách sinh viên có nguy cơ cao, hệ thống sẽ tạo một thông báo tổng hợp và gửi qua SNS.

### Gửi cảnh báo tự động

SNS nhận message từ Lambda và tự động gửi email đến giảng viên, giúp việc theo dõi sinh viên có nguy cơ không cần thực hiện thủ công.