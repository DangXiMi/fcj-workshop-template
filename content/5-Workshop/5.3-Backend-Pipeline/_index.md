---
title: "Core Backend & Data Pipeline"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---

In this section we build the serverless data pipeline: S3 storage, DynamoDB tables, the ingestion Lambda, and the read API.

```
CSV Upload → S3 (raw-data/) → Lambda → DynamoDB → API Gateway
```

#### Content

1. [Create S3 Buckets](5.3.1-S3/)
2. [Create DynamoDB Tables](5.3.2-DynamoDB/)
3. [Ingestion Lambda & S3 Trigger](5.3.3-Ingest-Lambda/)
4. [Read API with API Gateway](5.3.4-API-Gateway/)