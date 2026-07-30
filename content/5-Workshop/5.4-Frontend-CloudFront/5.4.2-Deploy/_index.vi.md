---
title: "Triển khai lên S3 + CloudFront"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 5.4.2. </b> "
---

#### Đóng gói (Build)

```bash
npm run build   # xuất ra thư mục dist/
```

#### Tải lên S3

Tải **nội dung** của thư mục `dist/` (bao gồm `index.html` và thư mục `assets/`) lên vị trí lưu trữ frontend, hoặc đồng bộ bằng AWS CLI:

```bash
aws s3 sync dist/ s3://student-warning-system/frontend/dist/ --delete
```

Bật tính năng **Static website hosting** trên S3 bucket (tệp chỉ mục là `index.html`) và thêm chính sách (bucket policy) cho phép truy cập công khai (public-read) cho đường dẫn chứa frontend.

#### Tạo CloudFront distribution

1. Truy cập **CloudFront → Create distribution**.
2. Origin domain: chọn **S3 static website endpoint** (`...s3-website-ap-southeast-1.amazonaws.com`), không phải REST endpoint của bucket.
3. Origin path: `/frontend/dist` (nếu bạn giữ nguyên cấu trúc thư mục này).
4. Viewer protocol policy: **Redirect HTTP to HTTPS**.
5. Default root object: `index.html`.

![CloudFront distribution]( /fcj-workshop-template/images/5-Workshop/5.4-Frontend-CloudFront/cloudfront.png)

#### Đấu nối tuyến đường SPA (SPA routing - quan trọng)

Các tuyến đường React Router như `/students` không tồn tại dưới dạng đối tượng S3 thực tế. Cần cấu hình phản hồi lỗi tùy chỉnh (custom error responses) để cơ chế điều hướng phía client (client-side routing) hoạt động chính xác:

| Mã lỗi HTTP (HTTP error code) | Trang phản hồi (Response page) | Mã phản hồi (Response code) |
|-----------------|---------------|---------------|
| 403 | `/index.html` | 200 |
| 404 | `/index.html` | 200 |

#### Xóa bộ nhớ đệm (Invalidate cache) sau mỗi lần triển khai

```bash
aws cloudfront create-invalidation --distribution-id <dist-id> --paths "/*"