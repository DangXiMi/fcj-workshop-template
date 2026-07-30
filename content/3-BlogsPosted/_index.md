---
title: "Blogs Posted"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3. </b> "
---


### [Blog 1 - Deploy XGBoost Serverless on AWS SageMaker](3.1-Blog1/)

This blog shares the journey of deploying an XGBoost model from AWS Lambda to SageMaker Serverless Inference. Initially, the author attempted to deploy using Lambda but encountered the 250 MB layer size limit due to large ML libraries (XGBoost, NumPy, SciPy). After realizing Lambda wasn't suitable for this use case, they switched to SageMaker Serverless Inference—a fully managed service that automatically scales based on requests and scales to zero when idle. The blog covers the deployment process including model standardization to XGBoost native format, preparing the inference package, building inference logic, and configuring the serverless endpoint. The result was a cost-effective, scalable solution that eliminated infrastructure management overhead.

### [Blog 2 - Building an Automated Batch Prediction System with Amazon S3, AWS Lambda and SageMaker](3.2-Blog2/)
**Status:** *Waiting for admin approval*  


This blog explains how to build an event-driven batch prediction pipeline for scenarios where educators need to evaluate hundreds of students at once rather than making real-time predictions one by one. The system allows lecturers to simply upload a CSV file to Amazon S3, which automatically triggers an AWS Lambda function. Lambda reads the file, preprocesses the data, invokes the SageMaker Serverless Endpoint for each student, classifies high-risk students based on a predefined threshold, and sends a summary report via email. The blog also covers challenges encountered including Lambda timeout configuration and IAM permissions setup, along with the solutions implemented.

### [Blog 3 - Automated Email Alerts with AWS SNS](3.3-Blog3/)
**Status:** *Waiting for admin approval*  

This blog discusses how AWS SNS (Simple Notification Service) was integrated into the batch prediction system to automatically send alert emails to lecturers when high-risk students are identified. SNS provides a pub/sub messaging service that allows notifications to be sent to multiple subscribers via email, SMS, or HTTP endpoints. The blog covers the step-by-step implementation: creating an SNS Topic, configuring email subscriptions (including the confirmation step), setting up IAM permissions for Lambda to publish messages, and integrating SNS into the workflow. A common pitfall—forgetting to confirm email subscriptions—is also highlighted with a practical solution.