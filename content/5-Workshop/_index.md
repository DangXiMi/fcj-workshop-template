---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
includeInReport: false
---


# Student Performance Early Warning System on AWS

#### Overview

The **Student Performance Early Warning System (SP-EWS)** is a cloud-native Information System built entirely on AWS. It ingests academic and behavioral data of students, predicts which students are at academic risk using a Machine Learning model, and presents the results through a Decision-Support-System (DSS) style dashboard with automated email alerts for high-risk students.

In this workshop, you will build the system end-to-end using AWS serverless and managed services. You will start from an empty AWS account and progressively deploy:

+ A **serverless data pipeline** that ingests a CSV dataset into DynamoDB.
+ A **REST API** built with API Gateway and Lambda.
+ A **React dashboard** hosted on Amazon S3 and delivered through Amazon CloudFront.
+ A **Machine Learning inference workflow** using an Amazon SageMaker endpoint (XGBoost) for batch and on-demand risk prediction.
+ **Email alerting** with Amazon SNS and **observability** with Amazon CloudWatch.
+ A complete **cleanup** procedure to avoid unnecessary charges.

The project follows the AWS Well-Architected Framework and covers architecture, deployment, ML integration, monitoring, security, cost optimization, testing, and cleanup.

{{< figure src="/fcj-workshop-template/images/2-Proposal/architecture.jpg" width="800" >}}

#### Content

1. [Workshop Overview](5.1-workshop-overview/)
2. [Prerequisites](5.2-prerequiste/)
3. [Core Backend & Data Pipeline](5.3-Backend-Pipeline/)
4. [Frontend Dashboard & CloudFront](5.4-Frontend-CloudFront/)
5. [Machine Learning Integration](5.5-ML-Integration/)
6. [Monitoring & Alerts](5.6-Monitoring-Alerts/)
7. [Clean up](5.7-Cleanup/)