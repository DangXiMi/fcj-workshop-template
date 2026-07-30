---
title: "Tích Hợp Kết Quả Dự Báo Vào Dashboard"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 5.5.4. </b> "
---

Thay thế logic giả lập rủi ro tạm thời bằng kết quả dự báo thực tế. Tạo hàm `getPredictionsFunction` (`GET /predictions`) để đọc dữ liệu từ bảng `prediction_results`, sau đó kết hợp (join) dữ liệu này với `student_records` theo trường `student_id` ở phía frontend.

```javascript
// kết hợp danh sách sinh viên với kết quả dự báo
const predMap = {};
predictions.forEach((p) => { predMap[String(p.student_id)] = p; });
const merged = students.map((s) => {
  const pred = predMap[String(s.student_id)];
  return { ...s, at_risk: pred ? pred.prediction : s.at_risk,
                 probability: pred ? pred.probability : null };
});
```

Bảng điều khiển giờ đây hiển thị mức độ nguy cơ và xác suất rủi ro thực tế từ mô hình ML; biểu mẫu Thêm Sinh viên (Add-Student) sẽ chạy dự báo trực tiếp, và trang Dự báo (Predict page) sẽ thực hiện suy luận theo yêu cầu (on-demand inference).

![Dashboard with real predictions]( /images/5-Workshop/5.5-ML/dashboard-predictions.png)

Tiến hành đóng gói và triển khai lại ứng dụng frontend, sau đó làm mới bộ nhớ đệm (invalidate cache) trên CloudFront (xem phần 5.4.2).