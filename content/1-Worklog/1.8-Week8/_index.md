---
title: "Week 8 Worklog"
date: 2026-07-20
weight: 8
chapter: false
build:
  list: always
  render: always
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives:

* Consolidate all learned skills into an end‑to‑end serverless AI project
* Build a complete Student Performance Early Warning System from data ingestion to deployment
* Apply serverless architecture, Machine Learning, and AWS services
* Deliver final presentation and documentation

### Tasks Carried Out This Week (July 20 – July 31):

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| 1–2 | **Final Project Kick‑off:** <br>&emsp; + Define project scope and requirements <br>&emsp; + Design architecture diagram (AWS Serverless) <br>&emsp; + Choose data sources and ML problem (XGBoost) | 20/07/2026 | 21/07/2026 | Project Guidelines |
| 3–4 | **Data Preparation & EDA:** <br>&emsp; + Clean and transform student dataset <br>&emsp; + Perform Exploratory Data Analysis (EDA) <br>&emsp; + Feature selection and engineering | 22/07/2026 | 23/07/2026 | Training Notebook |
| 5–6 | **Model Development & Training:** <br>&emsp; + Train XGBoost model locally (scikit-learn) <br>&emsp; + Evaluate model (99.67% accuracy, AUC-ROC: 1.0) <br>&emsp; + Convert to native XGBoost format for SageMaker | 24/07/2026 | 25/07/2026 | SageMaker notebooks |
| 7–8 | **Model Deployment & Serverless API:** <br>&emsp; + Deploy model to SageMaker Serverless Endpoint <br>&emsp; + Build Lambda functions (CRUD + Prediction) <br>&emsp; + Create API Gateway REST API <br>&emsp; + Configure S3 Trigger for batch processing | 26/07/2026 | 27/07/2026 | MLOps workshops |
| 9–10 | **Application Integration & Frontend:** <br>&emsp; + Develop Lambda functions: 7 functions (CRUD + Predictions) <br>&emsp; + Build React Dashboard (S3 + CloudFront) <br>&emsp; + Integrate SNS email alerts for high-risk students | 28/07/2026 | 29/07/2026 | Serverless workshops |
| 11–12 | **Testing, Monitoring & Documentation:** <br>&emsp; + Write unit and integration tests <br>&emsp; + Set up CloudWatch dashboards and alarms (9 alarms) <br>&emsp; + Prepare final documentation and presentation | 30/07/2026 | 31/07/2026 | Monitoring modules |

### Week 8 Achievements:

#### Final Project: "Student Performance Early Warning System (SP-EWS)"

**Architecture Overview:**
- **Frontend:** React Dashboard hosted on S3 + CloudFront (CDN)
- **API:** Amazon API Gateway (REST API) – 6 endpoints
- **Compute:** AWS Lambda (7 functions – CRUD + Predictions)
- **ML Model:** XGBoost (99.67% accuracy) deployed on SageMaker Serverless
- **Database:** Amazon DynamoDB (2 tables: `student_records`, `prediction_results`)
- **Storage:** Amazon S3 (Frontend hosting, CSV uploads, model artifacts)
- **Batch Processing:** S3 Trigger → Lambda (predictRiskFunction) → SageMaker → SNS
- **Real-time Prediction:** Lambda (predictRiskOnDemand) → SageMaker → JSON Response
- **Notifications:** Amazon SNS (Email alerts for high-risk students)
- **Monitoring:** Amazon CloudWatch (Logs, Metrics, 9 Alarms)
- **Security:** IAM Least Privilege

#### Key Project Deliverables:
* **Code Repository:** All Lambda functions, React frontend, and training notebook on GitHub
* **AWS Infrastructure:** Fully deployed serverless system with 9 AWS services
* **Live Demo:** React dashboard accessible via CloudFront URL
* **Documentation:** Complete workshop guide (10 sections), architecture diagram, and setup instructions
* **Presentation:** 30‑minute walkthrough covering decisions, challenges, and outcomes
* **Blog Posts:** 3-part series (SageMaker Serverless, Batch Processing, SNS Alerts)

### Key Learning Outcomes:

> **Final Reflection:** The 8‑week journey covered the entire AI/ML landscape on AWS – from foundational services to advanced MLOps and serverless integration. I have gained hands‑on experience in building production‑ready AI systems, following best practices for security, scalability, and maintainability. The internship provided a solid foundation for a career as an AI Engineer on the AWS platform.

> **Key Lessons Learned:**
> 1. **Lambda Layer Limitation:** Trying to package ML libraries (`xgboost`, `joblib`, `numpy`) in Lambda layers hit the 250 MB limit → switched to SageMaker Serverless.
> 2. **Feature Consistency:** Features must be sent to SageMaker in the exact same order and format as training (raw values, no normalization).
> 3. **Batch Processing:** Processing 3,000 students requires `BATCH_SIZE=500` to avoid Lambda timeouts.
> 4. **SNS Confirmation:** Email subscriptions require manual confirmation (check spam folder).
> 5. **Serverless Cost:** Total monthly cost ~$0.05 – $0.10 (scales to zero when idle).
> 6. **End-to-End Integration:** Real-time prediction (API Gateway → Lambda → SageMaker) + Batch prediction (S3 Trigger → Lambda → SageMaker → SNS) working together.

### AWS Services Used:

| Service | Purpose |
| :--- | :--- |
| **S3** | Frontend hosting, CSV uploads, model artifacts |
| **CloudFront** | CDN for React dashboard |
| **API Gateway** | REST API (6 endpoints) |
| **Lambda** | 7 serverless functions (CRUD + Predictions) |
| **DynamoDB** | 2 tables: `student_records`, `prediction_results` |
| **SageMaker** | Serverless XGBoost endpoint |
| **SNS** | Email alerts for high-risk students |
| **CloudWatch** | Logs, metrics, 9 alarms |
| **IAM** | Security and least privilege |