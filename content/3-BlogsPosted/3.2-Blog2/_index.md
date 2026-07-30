---
title: "Building an Automated Batch Prediction System with Amazon S3, AWS Lambda and SageMaker"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---


## Introduction

In the previous article, I shared how to deploy an XGBoost model on AWS SageMaker Serverless for real-time inference. This solution works well when the system needs to predict for individual students directly on the dashboard.

However, while working with lecturers, I identified another requirement:

> **Lecturers often want to evaluate an entire class or hundreds of students at once** rather than entering each student individually for prediction.

If we continued using the real-time API, the backend would have to send hundreds of sequential requests to SageMaker, which is time-consuming and inconvenient for users.

Therefore, I decided to build a batch prediction pipeline following an **event-driven** architecture, where lecturers only need to upload a CSV file and the entire processing happens automatically.

## The Problem

The system's objectives were:

- Lecturers only need to upload a CSV file containing the student list.
- The system automatically reads the data and performs predictions for each student.
- Aggregates the list of students at high academic risk.
- Sends results via email after processing is complete.
- No need to run a server continuously to save costs.

## Why I Chose AWS Lambda?

Since I already had a SageMaker Serverless Endpoint from the previous article, I needed a service that could:

- Automatically trigger when a new file arrives.
- Read data from Amazon S3.
- Call SageMaker for predictions.
- Process results.
- Send email notifications.

**AWS Lambda** met all these requirements perfectly.

What I liked most was Lambda's **event-driven** mechanism. Instead of the backend constantly checking for new files, Lambda is only triggered when Amazon S3 emits an upload event. This significantly reduces maintained resources and keeps the architecture simple.

## Challenges Encountered

During implementation, I faced two main issues.

### 1. Lambda Timeout

Lambda's default timeout is only about **3 seconds**. However, a CSV file could contain hundreds of students, and Lambda needs to:
- Read the file,
- Process data,
- Call SageMaker multiple times,
- Aggregate results,
- Send email.

The total processing time could be much longer than the default configuration.

**Solution:** I increased Lambda's timeout to **5 minutes**, sufficient for processing files appropriate to the project's scale.

### 2. IAM Permissions Configuration

Lambda needs to interact with multiple AWS services, so proper permissions are required.

Lambda's IAM Role was configured to:
- Read files from Amazon S3.
- Invoke SageMaker Endpoint.
- Send email via Amazon SNS.
- Write logs to Amazon CloudWatch for monitoring.

If any permission is missing, the entire pipeline stops at the corresponding step.

## How I Implemented It

### 1. Trigger Lambda When a New File Arrives

First, I configured **Amazon S3 Event Notification** so that whenever a new CSV file is uploaded to the bucket, Lambda is automatically triggered. This means users don't need to click a "Run Prediction" button or call any additional API.

### 2. Read Data from CSV File

Once triggered, Lambda retrieves the bucket name and file key from the S3 event. Lambda reads the CSV content and converts each row into student information. In this step, I also validated input data to avoid missing columns or incorrect formats.

### 3. Prepare Data for the Model

The XGBoost model requires input data to have the exact order and number of features as during training. Therefore, Lambda performs necessary preprocessing before sending data to SageMaker. Keeping the processing pipeline consistent between training and inference helps minimize prediction errors.

### 4. Call SageMaker Serverless Endpoint

For each student, Lambda sends a request to the SageMaker Endpoint via the `InvokeEndpoint` API. The XGBoost model returns the probability of the student belonging to the high-risk group. Lambda then processes this result for the classification step.

### 5. Classify At-Risk Students

After receiving the prediction probability, Lambda compares it with the **risk threshold** established during model evaluation. Students exceeding the threshold are added to the monitoring list. At the end of processing, Lambda generates a summary report including:
- Total number of students analyzed.
- Number of students at high academic risk.
- List of students requiring attention.

## Results Achieved

- **Successfully built an automated batch prediction pipeline** following event-driven architecture.
- Automatically triggers processing when a new CSV file is uploaded to Amazon S3.
- Performs predictions for the entire student list using SageMaker Serverless Endpoint.
- Automatically aggregates the list of high-risk students.
- Sends results via email after processing completes.
- **Reduces manual operations**, saves operational costs, and scales easily.
