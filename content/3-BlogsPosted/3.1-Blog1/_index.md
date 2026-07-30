---
title: "Deploy XGBoost Serverless on AWS SageMaker: Journey from Lambda to SageMaker Serverless"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

## Introduction

During my internship, I participated in developing an early warning system for students at risk of low academic performance. One of the critical components of the system was an XGBoost model used to predict the probability of students being at risk of poor academic performance based on learning and training data.

After completing model training, the next challenge was how to deploy the model as an API so that the website could send data and receive real-time prediction results.

## The Problem

The project requirements were clear:

- Have an API for frontend or backend to call predictions.
- Low cost since this was an internship project.
- No need to maintain an EC2 instance running 24/7.
- Ability to scale when many requests come in, but nearly zero cost when not in use.

Initially, I thought of **AWS Lambda** because it's a familiar serverless service that charges only per execution.

## Trying to Deploy with AWS Lambda

The initial idea was simple:

- Package the XGBoost model.
- Include libraries like xgboost, numpy, joblib in Lambda Layer.
- Lambda receives the request, loads the model, and returns prediction results.

However, when I started packaging, I encountered a common issue with Machine Learning applications:

> **The total size of the Lambda Layer exceeded the 250 MB limit after extraction.**

ML libraries like XGBoost, NumPy, and SciPy are quite large. Although there are optimization methods or using container images for Lambda, they all made the deployment process more complex than the project required.

At this point, I realized Lambda was not the right choice for this use case.

## Why I Switched to SageMaker Serverless?

After researching AWS services for Machine Learning, I decided to use **AWS SageMaker Serverless Inference**.

The reasons I chose this service were:

- **No server management required.**
- **No need to build the XGBoost runtime environment** – AWS already provides a container for XGBoost inference.
- **Endpoint auto-scales** based on request volume.
- When there are no requests, the endpoint can **scale to zero**, so no need to maintain continuous resources.

This allowed me to focus on the model rather than dealing with infrastructure issues.

## Implementation Process

### 1. Model Standardization

During training, I saved the model using Python for convenience during experimentation. However, when deploying on SageMaker, I converted the model to XGBoost's native format using Booster.save_model() to ensure SageMaker's XGBoost container could load it directly without depending on the Python training environment. This also made the deployment more stable.

### 2. Preparing the Deployment Package

After having the model, I packaged the necessary components for SageMaker inference, including:

- Model file (XGBoost native format).
- Data preprocessing file.
- Logic to convert requests to the format XGBoost can predict on.
- Logic to process output results.

The package was then uploaded to **Amazon S3** for SageMaker to use during Endpoint creation.

### 3. Building Inference Logic

I built an inference.py file so SageMaker knows how to process requests. This file performs the following steps:

1. Receives JSON data from the backend.
2. Converts the data to the format XGBoost requires (e.g., array of numbers).
3. Performs prediction.
4. Returns the prediction probability as JSON.

This way, the backend only needs to send data and receive results without worrying about how the model works internally.

### 4. Deploying Serverless Endpoint

After preparing the model and inference code, I created the SageMaker Serverless Endpoint with the following configuration:

- **Memory:** 1024 MB
- **Endpoint mode:** Serverless

Once the endpoint was successfully created, the backend only needed to call SageMaker's API whenever a prediction was needed. AWS automatically allocates resources when there are requests and releases them when there is no traffic.

## Results

After switching to SageMaker Serverless:

- No more Lambda Layer size limitations.
- No need to build the XGBoost runtime environment.
- Endpoint runs stably and can serve real-time predictions.
- No need to maintain a continuously running server, suitable for an internship project's scale.

## Key Takeaways

- **Lambda is not always suitable for ML workloads** due to layer size limits and execution time constraints.
- **SageMaker Serverless Inference** is the optimal solution for ML applications with low or intermittent traffic.
- **Standardizing models** to the framework's native format simplifies the deployment process.
- **Separating inference logic** (inference.py) makes maintenance and upgrades easier.