---
title: "Week 7 Worklog"
date: 2026-07-13
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives:

* Master event‑driven architectures for AI applications
* Use Amazon EventBridge for event routing
* Build workflows with AWS Step Functions
* Implement messaging with SQS and SNS
* Integrate all into a cohesive AI‑driven application

### Tasks Carried Out This Week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| 1 | **Amazon EventBridge:** <br>&emsp; + Event buses and rules <br>&emsp; + Event patterns and filtering <br>&emsp; + Targets (Lambda, Step Functions, SNS) | 13/07/2026 | 13/07/2026 | EventBridge Docs |
| 2 | **AWS Step Functions:** <br>&emsp; + State machines and workflows <br>&emsp; + Task, choice, parallel, wait states <br>&emsp; + Error handling and retries | 14/07/2026 | 14/07/2026 | Step Functions Workshop |
| 3 | **Workflow Orchestration with Step Functions:** <br>&emsp; + Orchestrate ML workflows (data prep, training, deployment) <br>&emsp; + Integrate with SageMaker, Lambda, Glue <br>&emsp; + Monitoring and logging | 15/07/2026 | 15/07/2026 | Step Functions ML |
| 4 | **Messaging with SQS and SNS:** <br>&emsp; + Queue vs. pub/sub patterns <br>&emsp; + SQS dead‑letter queues and visibility timeout <br>&emsp; + SNS filtering and fan‑out | 16/07/2026 | 16/07/2026 | SQS/SNS Docs |
| 5 | **Event Processing with SQS and SNS (Book Store Series):** <br>&emsp; + Decouple microservices for order processing <br>&emsp; + Use SQS for asynchronous tasks (e.g., image processing) <br>&emsp; + Notify customers via SNS | 17/07/2026 | 17/07/2026 | Book Store Series - Part 6 |
| 6 | **Build Event‑Driven AI Pipeline:** <br>&emsp; + Combine EventBridge, Step Functions, SQS, and AI services <br>&emsp; + Create a document processing system with AI enrichment | 18/07/2026 | 18/07/2026 | Document Management Series |

### Week 7 Achievements:

#### Amazon EventBridge
* Created custom event buses and defined schemas
* Set up rules to route events based on patterns
* Triggered Lambda and Step Functions in response to events
* Integrated with third‑party SaaS applications via partner events

#### AWS Step Functions
* Designed state machines for complex orchestration:
  - Parallel processing of multiple tasks
  - Choice states for conditional branching
  - Wait states for delayed execution
  - Catch and retry policies for fault tolerance
* Integrated with SageMaker for training and inference workflows
* Used CloudWatch to monitor state machine executions

#### Messaging Services
* Implemented SQS queues for decoupling and load leveling
* Configured dead‑letter queues and alarm on message age
* Published to SNS topics and subscribed with email, SMS, and Lambda
* Used SNS filtering to send messages to specific subscribers

#### Event‑Driven AI Document Processing
* Built a pipeline:
  1. Document uploaded to S3 → EventBridge rule
  2. Step Functions start execution: extract text, perform NLP (Comprehend), translate, summarize
  3. Results stored in S3 and notifications sent via SNS
* Used SQS to queue long‑running tasks (e.g., heavy ML inference)

### Key Learning Outcomes:

> **Key Insight:** Event‑driven architectures and workflow orchestration are key to building scalable, resilient AI applications. Step Functions handles complex state management, while SQS/SNS decouple components. Combining these with AI services allows for reactive, intelligent systems.