---
title: "Xây dựng React Dashboard"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 5.4.1. </b> "
---

#### Khởi tạo ứng dụng (Scaffold)

```bash
cd frontend
npm create vite@latest .   # chọn React
npm install
npm install axios recharts react-router-dom
```

#### API service

`src/services/api.js`:

```javascript
import axios from "axios";

const API_URL = "https://<api-id>.execute-api.ap-southeast-1.amazonaws.com/dev";

export const getStudents = () => axios.get(`${API_URL}/students`);
export const getPredictions = () => axios.get(`${API_URL}/predictions`);
export const predictRisk = (f) => axios.post(`${API_URL}/predict`, f);
export const createStudent = (s) => axios.post(`${API_URL}/students`, s);
export const updateStudent = (id, u) => axios.put(`${API_URL}/students/${id}`, u);
export const deleteStudent = (id) => axios.delete(`${API_URL}/students/${id}`);
```

#### Các phần của Dashboard 

Bảng điều khiển được tổ chức như một công cụ hỗ trợ ra quyết định (Decision-Support Tool):

- **Thẻ KPI** — tổng số sinh viên, số sinh viên có nguy cơ, điểm thi trung bình, tỷ lệ chuyên cần trung bình.
- **Phân bố nguy cơ** — biểu đồ tròn (nguy cơ vs. an toàn).
- **Bảng sinh viên nguy cơ cao** — danh sách các sinh viên cần hỗ trợ can thiệp.
- **Trang sinh viên (Students page)** — tìm kiếm, lọc, phân trang và các thao tác CRUD.
- **Trang dự báo (Predict page)** — dự báo nguy cơ theo yêu cầu mà không lưu vào cơ sở dữ liệu.

Trước khi khởi tạo SageMaker ML endpoint, bạn có thể sử dụng logic giả lập (mock risk logic) tạm thời để kiểm thử toàn bộ luồng frontend end-to-end; logic này sẽ được thay thế bằng kết quả dự báo thực tế trong phần 5.5.

![Dashboard overview]( /fcj-workshop-template/images/5-Workshop/5.4-Frontend-CloudFront/dashboard.png)

#### Chạy ứng dụng ở máy cục bộ

```bash
npm run dev
# http://localhost:5173
```