---
title: "Create S3 Buckets"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 5.3.1. </b> "
---

Create a **private** bucket for datasets and model artifacts.

1. **S3 → Create bucket**.
2. Bucket name: `student-warning-system` (globally unique — add a suffix if taken).
3. Region: `ap-southeast-1`.
4. Keep **Block all public access = ON** (dataset must remain private).

Create the following prefixes (folders):

```text
raw-data/          # ingestion input
frontend/          # store frontend dist
model/             # ML model artifacts
```


![S3 bucket structure]( /images/5-Workshop/5.3-Backend-Pipeline/s3-structure.png)