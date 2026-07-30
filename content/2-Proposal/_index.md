---
title: "Proposal"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
includeInReport: false
---

In this section, our group summarizes the contents of the project that we **plan** to conduct during the First Cloud AI Journey (FCAJ) internship.

# Student Performance Early Warning System
## A Serverless AWS Solution for Predicting and Alerting Academic Risk

### 1. Executive Summary

The **Student Performance Early Warning System (SP-EWS)** is a cloud-native Information System built to help lecturers and academic staff identify students at risk of poor academic performance **before** it is too late to intervene. The system ingests academic and behavioral data for roughly 3,000 students, predicts which students are at risk using a Machine Learning model, and presents the results through a Decision-Support-System (DSS) style dashboard with automated email alerts for high-risk students.

The platform is built entirely on AWS serverless and managed services — Amazon S3, AWS Lambda, Amazon DynamoDB, Amazon API Gateway, Amazon SageMaker (Serverless Inference), Amazon CloudFront, Amazon SNS, and Amazon CloudWatch — following the AWS Well-Architected Framework. Because every layer is serverless (including SageMaker Serverless Inference, which is billed only per request), operational cost is minimal and there is no idle compute charge.

### 2. Problem Statement

#### What's the Problem?

In many schools and training centers, student performance is tracked manually across spreadsheets and disconnected systems. As class sizes grow, lecturers detect struggling students too late, and academic intervention often happens after it is no longer effective. There is no centralized system that consolidates student data, automatically flags at-risk students, or provides an at-a-glance view for decision making.

#### The Solution

SP-EWS provides a centralized, automated pipeline:

- A CSV dataset is uploaded to **Amazon S3**, which triggers an **AWS Lambda** ingestion function that writes records to **Amazon DynamoDB**.
- A batch-prediction Lambda calls an **Amazon SageMaker Serverless Inference** endpoint (XGBoost) to compute a risk probability per student and stores the results in DynamoDB.
- An **Amazon API Gateway** REST API exposes the data, and a **React** dashboard hosted on **Amazon S3 + CloudFront** visualizes KPIs, risk distribution, and the list of high-risk students.
- **Amazon SNS** sends email alerts for high-risk students, and **Amazon CloudWatch** provides logs, metrics, and alarms.

Lecturers can also add, edit, and delete student records and run on-demand predictions for a single student without saving.

#### Benefits and Return on Investment

The system replaces manual review with an automated early-warning workflow, allowing timely academic intervention. It centralizes student data, improves data reliability, and provides a reusable data and ML foundation for future academic analytics projects. Because the architecture is fully serverless and uses SageMaker Serverless Inference (pay-per-request, no 24/7 instance cost), the running cost stays within the AWS Free Tier for a workload of this size and usage pattern. The main return is the time saved by lecturers and the earlier detection of at-risk students.

### 3. Solution Architecture

The platform uses an end-to-end serverless architecture. Data flows from CSV upload through ingestion, prediction, storage, and API, and is presented on a React dashboard delivered through CloudFront:

```
CSV Dataset
    ↓
Amazon S3 (raw-data / predict-input / model)
    ↓
AWS Lambda (ingest + batch predict)
    ↓
Amazon DynamoDB (student_records + prediction_results)
    ↓
Amazon API Gateway (REST)
    ↓
React Dashboard (Amazon S3 + CloudFront)

Amazon SageMaker Serverless Inference (XGBoost)  →  Risk probability
Amazon SNS                                       →  High-risk email alerts
Amazon CloudWatch                                →  Logs, metrics, alarms
```

{{< figure src="/fcj-workshop-template/images/5-Workshop/5.1-Workshop-overview/Solution_Archi.jpg" width="800" >}}


#### AWS Services Used

- **Amazon S3**: Stores the dataset, prediction input, model artifacts, and the frontend build.
- **AWS Lambda**: Handles ingestion, batch prediction, on-demand prediction, and CRUD logic.
- **Amazon DynamoDB**: Stores `student_records` and `prediction_results` (on-demand capacity mode).
- **Amazon API Gateway**: Exposes the REST API consumed by the dashboard.
- **Amazon SageMaker (Serverless Inference)**: Serves the trained XGBoost risk-prediction model, billed per request.
- **Amazon CloudFront**: Delivers the React dashboard over HTTPS with caching.
- **Amazon SNS**: Sends email alerts for high-risk students.
- **Amazon CloudWatch**: Provides logs, metrics, and alarms.
- **AWS IAM**: Enforces least-privilege access for each Lambda function.

#### Component Design

- **Data Ingestion**: An upload to the `raw-data/` prefix triggers a Lambda that parses the CSV and writes records to `student_records`.
- **Machine Learning**: A batch-prediction Lambda (triggered by `predict-input/`) calls the SageMaker endpoint in batches, writing risk probabilities to `prediction_results`. An on-demand endpoint predicts a single student without saving.
- **Data Storage**: DynamoDB holds student records and prediction results; S3 holds datasets and model artifacts.
- **API Layer**: API Gateway with Lambda proxy integration exposes read, predict, and CRUD endpoints.
- **Web Interface**: A React dashboard on S3 + CloudFront presents KPIs, risk distribution, high-risk tables, and CRUD/predict pages.
- **Alerts & Monitoring**: SNS sends high-risk email summaries; CloudWatch alarms notify on Lambda errors and API 5XX responses.

### 4. Technical Implementation

**Implementation Phases**

The project follows four phases across the internship:

- **Design & Architecture**: Research the dataset, define the ML target (`at_risk`), and design the serverless architecture following the Well-Architected Framework.
- **Core Backend & Data Pipeline**: Build the S3 → Lambda → DynamoDB ingestion pipeline and the read API with API Gateway.
- **Frontend & ML Integration**: Build and deploy the React dashboard to S3 + CloudFront, deploy the SageMaker Serverless endpoint, and connect batch and on-demand prediction plus CRUD.
- **Monitoring, Hardening & Cleanup**: Add SNS alerts and CloudWatch alarms, apply Well-Architected improvements (IAM least-privilege, CORS tightening, S3 lifecycle, DLQ), perform failure testing, and document a full cleanup procedure.

**Technical Requirements**

- **Dataset**: ~3,000 student records with five core numeric features (`attendance_rate`, `assignment_avg_score`, `exam_avg_score`, `homework_submission_rate`, `class_participation`) and a binary `at_risk` label. Feature order must match the model training format for the CSV endpoint.
- **Model**: XGBoost binary classifier deployed as a SageMaker Serverless Inference endpoint (memory 1 GB, max concurrency 5).
- **Backend**: Python 3.12 Lambda functions. The ingestion function is packaged as a ZIP with `pandas`; the CRUD and on-demand predict functions use only `boto3`. Lambda proxy integration requires CORS headers to be returned from the Lambda code.
- **Frontend**: React (Vite) with axios and recharts, deployed to S3 static hosting and served through CloudFront with SPA routing (403/404 → `index.html`).
- **Region**: All resources are provisioned in **Asia Pacific (Singapore) `ap-southeast-1`** to avoid cross-region errors.

### 5. Timeline & Milestones

The internship runs for **12 weeks**, producing a working, testable increment each week:

- **Weeks 1–2**: AWS fundamentals, core services, and project scoping.
- **Weeks 3–4**: Architecture design, backend data pipeline (S3, DynamoDB, ingestion Lambda), and the Students API.
- **Weeks 5**: React dashboard and CloudFront deployment.
- **Weeks 6–8**: ML training, SageMaker endpoint deployment, batch prediction, and on-demand prediction + CRUD APIs with SNS alerts.
- **Weeks 9–10**: DSS dashboard enhancements and CloudWatch monitoring/alarms.
- **Weeks 11–12**: Testing, security review, cost optimization, bilingual documentation, cleanup, and the final workshop.

### 6. Budget Estimation

Because the architecture is fully serverless and SageMaker uses Serverless Inference (pay-per-request, no idle instance cost), the estimated monthly cost is minimal and largely within the AWS Free Tier for this workload.

#### Estimated Infrastructure Costs 

- **AWS Lambda**: ~$0.00/month (low invocation volume, within Free Tier).
- **Amazon DynamoDB (on-demand)**: ~$0.00–$0.10/month for ~3,000 records and light read/write.
- **Amazon S3**: ~$0.05/month (dataset, model artifacts, frontend assets).
- **Amazon API Gateway**: ~$0.01/month (low request volume).
- **Amazon CloudFront**: ~$0.00/month (within Free Tier for demo traffic).
- **Amazon SageMaker Serverless Inference**: billed only per request (compute duration + request count); no charge while idle.
- **Amazon SNS / CloudWatch**: ~$0.00/month within Free Tier.


### 7. Risk Assessment

#### Risk Matrix

- **Missing authentication on the API**: High impact, medium probability. The API Gateway endpoints (including DELETE) currently have no authentication.
- **Overly broad IAM permissions**: Medium impact, medium probability. Some roles use managed FullAccess policies rather than least-privilege.
- **SageMaker concurrency throttling**: Low impact, low probability. Max concurrency is 5; parallel batch calls could hit HTTP 429.
- **Cost overruns**: Low impact, low probability. Serverless usage stays within Free Tier for this workload.

#### Mitigation Strategies

- **Authentication**: Add an API Key + Usage Plan as a minimum, and upgrade to Amazon Cognito for real user authentication.
- **IAM**: Replace FullAccess policies with inline least-privilege policies scoped to specific actions and resource ARNs.
- **Concurrency**: Call the SageMaker endpoint in sequential batches (e.g., 6 batches of 500 for 3,000 records) rather than in parallel.
- **CORS & resilience**: Restrict CORS to the CloudFront domain, add an SQS Dead Letter Queue for the async batch-prediction Lambda, and apply S3 lifecycle policies.


### 8. Expected Outcomes

#### Technical Improvements

Automated, ML-based early warning replaces manual student review. Lecturers get a real-time DSS dashboard, on-demand risk prediction, and automated email alerts for high-risk students.

#### Long-term Value

The project delivers a reusable serverless and Machine Learning foundation for academic analytics, a bilingual (English/Vietnamese) workshop that documents the full build, and a Well-Architected review that identifies concrete production-readiness improvements (authentication, IAM least-privilege, IaC, DLQ) for future iterations.