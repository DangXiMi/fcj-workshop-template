---
title: "Week 2 Worklog"
date: 2026-06-08
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives:

* Master serverless automation with AWS Lambda
* Build serverless backends for AI applications
* Understand event-driven architecture
* Start building the Book Store Serverless project

### Tasks Carried Out This Week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| 1 | **Serverless Automation with AWS Lambda:** <br>&emsp; + Lambda runtime environments and supported languages <br>&emsp; + Function configuration and memory allocation <br>&emsp; + Triggers and event sources | 08/06/2026 | 08/06/2026 | Lambda Documentation |
| 2 | **Lambda Advanced:** <br>&emsp; + Layers and custom runtimes <br>&emsp; + Environment variables and secrets management <br>&emsp; + VPC integration and networking <br>&emsp; + Monitoring with CloudWatch | 09/06/2026 | 09/06/2026 | Lambda Best Practices |
| 3 | **Serverless Backend with Lambda, S3, and DynamoDB:** <br>&emsp; + Design serverless REST API architecture <br>&emsp; + Create Lambda functions for CRUD operations <br>&emsp; + Integrate with API Gateway | 10/06/2026 | 10/06/2026 | Book Store Series - Part 1 |
| 4 | **Frontend Development for Serverless APIs:** <br>&emsp; + Set up frontend project (React/JavaScript) <br>&emsp; + Connect frontend to API Gateway endpoints <br>&emsp; + Implement CRUD operations in frontend | 11/06/2026 | 11/06/2026 | Book Store Series - Part 2 |
| 5 | **Deployment Automation with AWS SAM:** <br>&emsp; + SAM template structure and syntax <br>&emsp; + Define resources (Lambda, API Gateway, DynamoDB) <br>&emsp; + Deploy and manage applications | 12/06/2026 | 12/06/2026 | AWS SAM Documentation |
| 6 | **User Authentication with Amazon Cognito:** <br>&emsp; + Configure Cognito User Pools <br>&emsp; + Set up authentication with Amplify <br>&emsp; + Implement sign-up, sign-in, and logout flows | 13/06/2026 | 13/06/2026 | Cognito Workshop |

### Week 2 Achievements:

#### AWS Lambda Expertise
* Created and deployed multiple Lambda functions
* Implemented functions in Python and Node.js
* Configured triggers from S3, API Gateway, and DynamoDB Streams
* Optimized performance through memory allocation tuning
* Managed dependencies using Lambda Layers

#### Serverless Backend Development
* Designed and implemented CRUD API using:
  - **API Gateway:** REST API with resources and methods
  - **Lambda:** Business logic for handling requests
  - **DynamoDB:** NoSQL database for data storage
* Implemented proper error handling and response formatting
* Added request validation and transformation

#### AWS SAM (Serverless Application Model)
* Created SAM templates with:
  - Globals section for shared configuration
  - Resource definitions with CloudFormation syntax
  - Event sources for Lambda triggers
* Deployed applications using `sam build` and `sam deploy`
* Tested locally using `sam local start-api`

#### User Authentication
* Set up Cognito User Pool with:
  - Custom attributes
  - Password policies
  - Multi-factor authentication (MFA) options
* Integrated Cognito with Amplify for frontend auth flows
* Implemented sign-up, sign-in, password reset, and logout

### Key Learning Outcomes:

> **Key Insight:** Serverless architectures allow AI applications to scale automatically and reduce operational overhead. Combining Lambda, API Gateway, and DynamoDB creates a cost-effective, resilient backend for ML-powered features.