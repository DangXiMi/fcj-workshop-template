---
title: "Week 6 Worklog"
date: 2026-07-06
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives:

* Implement CI/CD for AI/ML applications using AWS CodePipeline
* Automate build, test, and deployment of ML models
* Integrate with AWS CodeBuild and CodeDeploy
* Understand DevOps practices for MLOps

### Tasks Carried Out This Week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| 1 | **CI/CD Pipeline with AWS CodePipeline:** <br>&emsp; + Source stage (CodeCommit, GitHub) <br>&emsp; + Build stage (CodeBuild) <br>&emsp; + Deploy stage (CodeDeploy or custom) | 06/07/2026 | 06/07/2026 | CodePipeline Docs |
| 2 | **Automated Deployments with AWS CodePipeline:** <br>&emsp; + Integrate with SageMaker Pipelines <br>&emsp; + Trigger retraining on data changes <br>&emsp; + Deploy new models to endpoints | 07/07/2026 | 07/07/2026 | CI/CD Workshop |
| 3 | **DevOps with AWS CodePipeline:** <br>&emsp; + Use pipeline variables and artifacts <br>&emsp; + Add manual approval gates <br>&emsp; + Notifications and monitoring | 08/07/2026 | 08/07/2026 | DevOps with CodePipeline |
| 4 | **Infrastructure as Code with AWS CloudFormation:** <br>&emsp; + Design and deploy infrastructure stacks <br>&emsp; + Use parameters, outputs, and conditions <br>&emsp; + Manage stack updates and rollbacks | 09/07/2026 | 09/07/2026 | CloudFormation |
| 5 | **AWS CDK Essentials:** <br>&emsp; + Define infrastructure using TypeScript/Python <br>&emsp; + Create reusable constructs <br>&emsp; + Deploy stacks with CDK CLI | 10/07/2026 | 10/07/2026 | CDK Workshop |
| 6 | **Infrastructure as Code for ECS with CDK:** <br>&emsp; + Deploy containerized ML applications <br>&emsp; + Use CDK Pipelines for CI/CD | 11/07/2026 | 11/07/2026 | CDK for ECS |

### Week 6 Achievements:

#### CI/CD with CodePipeline
* Set up a pipeline with source (CodeCommit), build (CodeBuild), and deploy stages
* Integrated CodeBuild with Docker to build and push containers
* Deployed containerized applications to ECS/Fargate and SageMaker endpoints
* Added manual approval steps for production deployment

#### Automated ML Workflows
* Triggered SageMaker Pipeline execution from CodePipeline when new data arrives
* Used pipeline artifacts to pass model artifacts between stages
* Deployed approved models automatically to staging and production

#### Infrastructure as Code
* Learned CloudFormation: templates, stack operations, drift detection
* Created CloudFormation templates for:
  - VPC, subnets, security groups
  - SageMaker endpoints and IAM roles
  - Lambda functions and API Gateway
* Migrated to AWS CDK:
  - Defined stacks in Python
  - Used L2 constructs for higher‑level abstraction
  - Synthesized and deployed stacks

#### CDK Pipelines
* Built a CI/CD pipeline using CDK Pipelines
* Multi‑stage deployment (dev → test → prod)
* Automated infrastructure provisioning with every commit

### Key Learning Outcomes:

> **Key Insight:** CI/CD and Infrastructure as Code are essential for reliable, repeatable ML deployments. Using CodePipeline and CDK enables teams to treat ML models as code, with versioning, testing, and automated rollouts, reducing manual errors and speeding up delivery.