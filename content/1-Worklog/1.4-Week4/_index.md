---
title: "Week 4 Worklog"
date: 2026-07-06
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:

* Explore AWS AI services for image, text, and speech analysis
* Integrate Rekognition, Comprehend, Translate, and Polly into applications
* Build a multi‑modal AI application
* Understand security and governance for AI services

### Tasks Carried Out This Week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| 1 | **Amazon Rekognition:** <br>&emsp; + Image and video analysis <br>&emsp; + Face detection, comparison, and search <br>&emsp; + Custom labels (training) | 06/07/2026 | 06/07/2026 | Rekognition Docs |
| 2 | **Amazon Comprehend:** <br>&emsp; + Natural language processing (NLP) <br>&emsp; + Entity recognition, key phrases, sentiment <br>&emsp; + Custom classification and entity recognition | 07/07/2026 | 07/07/2026 | Comprehend Docs |
| 3 | **Amazon Translate & Polly:** <br>&emsp; + Language translation with Translate <br>&emsp; + Text‑to‑speech with Polly (neural voices) <br>&emsp; + Use cases for localization and accessibility | 08/07/2026 | 08/07/2026 | Translate & Polly |
| 4 | **AWS AI Services Integration Workshop:** <br>&emsp; + Build a serverless application that uses Rekognition, Comprehend, and Translate <br>&emsp; + Process images and text in a pipeline | 09/07/2026 | 09/07/2026 | AI Services Workshop |
| 5 | **Security and Governance:** <br>&emsp; + IAM policies for AI services <br>&emsp; + AWS Firewall Manager and GuardDuty <br>&emsp; + Data privacy and encryption (KMS) | 10/07/2026 | 10/07/2026 | Security Modules |
| 6 | **SageMaker with AI Services:** <br>&emsp; + Combine built‑in algorithms with AI services for hybrid solutions <br>&emsp; + Model explainability with SageMaker Clarify | 11/07/2026 | 11/07/2026 | SageMaker Clarify |

### Week 4 Achievements:

#### ✅ Amazon Rekognition
* Detected objects, scenes, and faces in images and videos
* Performed face comparison and matching against a collection
* Created a custom label model to detect specific objects (e.g., defects)
* Used Rekognition Video for streaming event analysis

#### ✅ Amazon Comprehend
* Extracted entities, key phrases, and sentiment from text
* Built a custom classifier for product categories
* Created custom entity recognizer for domain‑specific terms
* Integrated with S3 and Lambda for automated text analysis

#### ✅ Amazon Translate and Polly
* Translated content between multiple languages using Translate
* Generated lifelike speech with Polly’s neural voices
* Used SSML to control pronunciation and prosody
* Built a multi‑lingual chat support prototype

#### ✅ Security & Governance
* Applied fine‑grained IAM policies for AI services
* Enabled CloudTrail and GuardDuty for threat detection
* Encrypted data at rest using KMS for S3 buckets and DynamoDB tables
* Set up AWS Firewall Manager to protect API Gateway endpoints

### Key Learning Outcomes:

> **Key Insight:** AWS AI services offer ready‑to‑use intelligence that can be quickly integrated into applications. They lower the barrier for adding AI capabilities, and when combined with security best practices, they provide a robust foundation for production workloads.