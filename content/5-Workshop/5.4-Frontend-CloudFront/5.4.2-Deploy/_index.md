---
title: "Deploy to S3 + CloudFront"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 5.4.2. </b> "
---

#### Build

```bash
npm run build   # outputs dist/
```

#### Upload to S3

Upload the **contents** of `dist/` (i.e. `index.html` and `assets/`) to the frontend location, or sync via CLI:

```bash
aws s3 sync dist/ s3://student-warning-system/frontend/dist/ --delete
```

Enable **Static website hosting** on the bucket (index document `index.html`) and add a public-read bucket policy for the frontend path.

#### Create the CloudFront distribution

1. **CloudFront → Create distribution**.
2. Origin domain: the **S3 static website endpoint** (`...s3-website-ap-southeast-1.amazonaws.com`), not the bucket REST endpoint.
3. Origin path: `/frontend/dist` (if you kept that layout).
4. Viewer protocol policy: **Redirect HTTP to HTTPS**.
5. Default root object: `index.html`.

![CloudFront distribution]( /fcj-workshop-template/images/5-Workshop/5.4-Frontend-CloudFront/cloudfront.png)

#### SPA routing (important)

React Router routes such as `/students` do not exist as S3 objects. Configure custom error responses so client-side routing works:

| HTTP error code | Response page | Response code |
|-----------------|---------------|---------------|
| 403 | `/index.html` | 200 |
| 404 | `/index.html` | 200 |

#### Invalidate cache after each deploy

```bash
aws cloudfront create-invalidation --distribution-id <dist-id> --paths "/*"
```

