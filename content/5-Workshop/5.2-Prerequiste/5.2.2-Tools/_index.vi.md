---
title: "Môi trường Phát triển Cục bộ"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 5.2.2. </b> "
---

Cài đặt các công cụ sau trên máy cục bộ của bạn:

| Công cụ | Mục đích |
|-----------------|---------|
| AWS CLI v2      | Truy cập và tự động hóa các thao tác trên AWS |
| Python 3.12     | Môi trường chạy Lambda và huấn luyện mô hình ML |
| Node.js ≥ 18    | Phát triển React frontend |
| Git             | Quản lý phiên bản mã nguồn (Version control) |
| Postman         | Kiểm thử API |
| VS Code/Pycharm | Trình soạn thảo mã nguồn |

#### Cấu hình AWS CLI

```bash
aws configure
```

Nhập các thông tin tương ứng:

```text
AWS Access Key ID: <access key của bạn>
AWS Secret Access Key: <secret key của bạn>
Default region name: ap-southeast-1
Default output format: json
```

Kiểm tra lại cấu hình:

```bash
aws s3 ls
```

#### Môi trường ảo Python (Virtual environment)

```bash
python -m venv .venv
# Trên Windows
.venv\Scripts\activate
pip install -r requirements.txt