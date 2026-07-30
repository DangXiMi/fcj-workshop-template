---
title: "Machine Learning Integration"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5.5. </b> "
---

Integrate the risk-prediction model: deploy the SageMaker endpoint, run batch prediction over the dataset, expose an on-demand prediction API, add CRUD, and send high-risk alerts.

```
Features → SageMaker Endpoint (XGBoost) → Risk probability
Batch  → prediction_results (DynamoDB) + SNS alert
On-demand → POST /predict
```

#### Content

1. [Model & SageMaker Endpoint](5.5.1-Model-Endpoint/)
2. [Batch Prediction Lambda](5.5.2-Batch-Predict/)
3. [On-Demand Prediction & CRUD APIs](5.5.3-Predict-CRUD/)
4. [Connect Predictions to the Dashboard](5.5.4-Dashboard-Integration/)