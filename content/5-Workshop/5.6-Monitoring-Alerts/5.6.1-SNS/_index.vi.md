---
title: "Cảnh báo Email qua SNS"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 5.6.1. </b> "
---

1. Truy cập **SNS → Topics → Create topic** (chọn loại Standard).
2. Chọn **Create subscription** → Giao thức (Protocol) **Email** → nhập địa chỉ email của bạn.
3. Xác nhận đăng ký nhận tin từ hộp thư đến (trạng thái bắt buộc phải chuyển sang **Confirmed**).

{{% notice info %}}
Nhật ký "publish succeeded" không đảm bảo tin nhắn đã được chuyển đến hộp thư. Dịch vụ SNS chỉ gửi email đến các địa chỉ đã được **xác nhận (confirmed)**. Nếu không nhận được email, hãy kiểm tra trạng thái đăng ký xem đã là Confirmed thay vì PendingConfirmation hay chưa.
{{% /notice %}}

Kiểm thử bằng tính năng **Publish message**, sau đó kiểm thử toàn trình (end-to-end) bằng cách tải lên một đợt dữ liệu có chứa sinh viên thuộc nhóm nguy cơ cao và xác nhận email tổng hợp đã gửi về hộp thư.

![SNS alert email]( /fcj-workshop-template/images/5-Workshop/5.6-Monitoring/sns-email.png)