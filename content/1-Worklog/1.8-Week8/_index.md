---
title: "Week 8 Worklog"
date: 2026-08-03
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
build:
  list: always
  render: always
---

### Week 8 Objectives:

* Consolidate all learned skills into an end‑to‑end AI project
* Build a complete AI application from data ingestion to deployment
* Apply MLOps, serverless, and AI services
* Deliver final presentation and documentation

### Tasks Carried Out This Week (August 3 – August 14):

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| 1–2 | **Final Project Kick‑off:** <br>&emsp; + Define project scope and requirements <br>&emsp; + Design architecture diagram <br>&emsp; + Choose data sources and ML problem | 03/08/2026 | 04/08/2026 | Project Guidelines |
| 3–4 | **Data Preparation & Feature Engineering:** <br>&emsp; + Use Glue and Athena to clean and transform data <br>&emsp; + Create feature groups in SageMaker Feature Store | 05/08/2026 | 06/08/2026 | Previous workshops |
| 5–6 | **Model Development & Training:** <br>&emsp; + Train multiple models (built‑in or custom) <br>&emsp; + Perform hyperparameter tuning <br>&emsp; + Evaluate and select best model | 07/08/2026 | 08/08/2026 | SageMaker notebooks |
| 7–8 | **MLOps Pipeline Setup:** <br>&emsp; + Build SageMaker Pipeline for automated retraining <br>&emsp; + Set up CI/CD with CodePipeline and CDK <br>&emsp; + Implement model registry and approval | 09/08/2026 | 10/08/2026 | MLOps workshops |
| 9–10 | **Application Integration & Frontend:** <br>&emsp; + Develop a serverless API (Lambda + API Gateway) <br>&emsp; + Build a frontend using React/Amplify <br>&emsp; + Integrate authentication (Cognito) and AI services | 11/08/2026 | 12/08/2026 | Serverless workshops |
| 11–12 | **Testing, Monitoring & Documentation:** <br>&emsp; + Write unit and integration tests <br>&emsp; + Set up CloudWatch dashboards and alerts <br>&emsp; + Prepare final documentation and presentation | 13/08/2026 | 14/08/2026 | Monitoring modules |

### Week 8 Achievements:

#### ✅ Final Project: "Intelligent Document Processing System"

**Architecture Overview:**
- **Data Lake:** S3 for raw and processed data
- **ETL:** AWS Glue (PySpark) for data transformation
- **Feature Store:** SageMaker Feature Store for feature reuse
- **Training:** SageMaker (XGBoost/Linear Learner) + Hyperparameter Tuning
- **MLOps:** SageMaker Pipelines + Model Registry + CI/CD (CodePipeline)
- **Inference:** Real‑time endpoints for predictions; batch inference via Step Functions
- **AI Services:** Comprehend for entity extraction, Translate for multi‑language support
- **Frontend:** React with Amplify (Cognito auth, API Gateway)
- **Orchestration:** Step Functions for complex workflows
- **Monitoring:** CloudWatch, X‑Ray for tracing, and SageMaker Model Monitor

#### Key Project Deliverables:
* **Code Repository:** All infrastructure as code (CDK) and application code on CodeCommit
* **CI/CD Pipeline:** Automated deployment of infra, model, and application
* **Live Demo:** Fully functional web application with AI capabilities
* **Documentation:** Architecture diagram, setup guide, and usage instructions
* **Presentation:** 30‑minute walkthrough covering decisions, challenges, and outcomes

### Key Learning Outcomes:

> **Final Reflection:** The 8‑week journey covered the entire AI/ML landscape on AWS – from foundational services to advanced MLOps and serverless integration. I have gained hands‑on experience in building production‑ready AI systems, following best practices for security, scalability, and maintainability. The internship provided a solid foundation for a career as an AI Engineer on the AWS platform.