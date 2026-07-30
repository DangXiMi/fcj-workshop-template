---
title: "Week 5 Worklog"
date: 2026-07-13
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Objectives:

* Dive deep into Amazon SageMaker advanced features
* Implement MLOps practices: Feature Store, Pipelines, Model Registry
* Explore model explainability and bias detection with Clarify
* Learn about SageMaker Edge Manager and Neo

### Tasks Carried Out This Week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| 1 | **SageMaker Feature Store:** <br>&emsp; + Create feature groups <br>&emsp; + Ingest, retrieve, and share features <br>&emsp; + Online vs. offline store | 13/07/2026 | 13/07/2026 | Feature Store Docs |
| 2 | **SageMaker Pipelines:** <br>&emsp; + Define end‑to‑end ML pipelines <br>&emsp; + Steps: processing, training, evaluation, deployment <br>&emsp; + Pipeline automation and orchestration | 14/07/2026 | 14/07/2026 | Pipelines Workshop |
| 3 | **Model Registry & Deployment:** <br>&emsp; + Register models with metadata <br>&emsp; + Approve models for deployment <br>&emsp; + Multi‑stage deployment (staging, production) <br>&emsp; + Blue/green and canary deployments | 15/07/2026 | 15/07/2026 | Model Registry |
| 4 | **SageMaker Clarify:** <br>&emsp; + Bias detection and measurement <br>&emsp; + Model explainability (SHAP) <br>&emsp; + Report generation and monitoring | 16/07/2026 | 16/07/2026 | Clarify Docs |
| 5 | **SageMaker Edge Manager & Neo:** <br>&emsp; + Compile models for edge devices <br>&emsp; + Deploy to edge with SageMaker Edge Manager <br>&emsp; + Monitor edge device models | 17/07/2026 | 17/07/2026 | Edge Manager |
| 6 | **Hands‑on: Build a Full MLOps Pipeline:** <br>&emsp; + Combine Feature Store, Pipelines, Registry, and Clarify <br>&emsp; + Automate retraining and deployment | 18/07/2026 | 18/07/2026 | MLOps Workshop |

### Week 5 Achievements:

#### ✅ SageMaker Feature Store
* Created feature groups for training and inference
* Ingested historical and real‑time features
* Retrieved feature values for model serving
* Understood the difference between online (low‑latency) and offline (batch) stores

#### ✅ SageMaker Pipelines
* Built a pipeline with steps:
  - Preprocessing (Scikit‑learn / Spark)
  - Training (built‑in or custom algorithm)
  - Evaluation (compare metrics against baseline)
  - Conditional step to register model if threshold met
* Scheduled pipeline execution using EventBridge
* Monitored pipeline runs via SageMaker Studio

#### ✅ Model Registry
* Registered model versions with custom metadata (accuracy, date, commit hash)
* Set approval statuses (pending, approved, rejected)
* Deployed approved models to endpoints with different aliases

#### ✅ SageMaker Clarify
* Analyzed training data for bias (pre‑training)
* Detected post‑training bias across protected groups
* Generated SHAP explanations to interpret predictions
* Produced reports that can be included in compliance documentation

#### ✅ Edge Deployment
* Used SageMaker Neo to compile models for edge devices (Raspberry Pi, Jetson Nano)
* Deployed compiled models to edge devices with SageMaker Edge Manager
* Tracked edge device fleet and model performance

### Key Learning Outcomes:

> **Key Insight:** MLOps is critical for production‑grade ML. SageMaker provides the tools to manage the entire lifecycle: features, pipelines, model versioning, monitoring, and explainability. This enables reproducible, auditable, and scalable ML workflows.