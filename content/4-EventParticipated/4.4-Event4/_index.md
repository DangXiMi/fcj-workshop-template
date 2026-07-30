---
title: "Event 4"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 4.4. </b> "
---

### Event Objectives

- Provide hands-on experience building AI agent applications
- Foster collaboration and networking among participants
- Allow teams to pitch projects to a panel of judges
- Encourage learning and practical application of AWS and AI technologies
- Demonstrate solving real-world business problems using AI agents

### Speakers

- **Nguyễn Gia Hưng** – Head of Solution Architect, AWS Vietnam
- **Joseph Marazota** – Head of Technology, Asia
- **Nguyễn Ngọc Hưng** – Solution Architect
- **Winning Team: One Team** – KFC Conversational Ordering Agent
- **Sign Signal C Team** – Competitive Intelligence Platform
- **Team 3K** – Smart Queue Management (Shepher)
- **Team Six Pillars** – Anti-Money Laundering (AML) System
- **Team BL** – Architecture & Cost Estimation Assistant

### Key Highlights

#### Opening Remarks (Joseph Marazota)

- AWS is investing heavily in young talent in Vietnam
- The industry is transforming rapidly; AI agents will handle releases potentially every minute
- Young professionals bring fresh mental models and aren't burdened by legacy thinking
- Robots without human direction are just hardware; agents refine and analyze data for improvement
- The next 2-3 years will see massive transformation across industries
- **Key Formula for Success:** Capability × Visibility × Consistency = Results

#### One Team: AI-Powered Conversational Ordering for KFC

**Business Problem:**
- McDonald's voice AI ordering failed due to hallucinations and inability to understand human conversation
- Traditional app ordering creates friction: users must leave conversation, download apps, create accounts, navigate complex menus
- Customer interest drops during the app-switching process

**Solution:**
- **Multi-channel conversational ordering agent** on Zalo (primary) and WhatsApp
- No app switching required; orders directly within chat platform
- No new account creation required
- Uses AI to extract customer intent and queries
- **Tiny Fish** for web scraping KFC's official website
- **AWS database** for data storage and retrieval
- Agent memory preserves previous orders and session context
- Order confirmation step prevents hallucinations (avoiding McDonald's 100-chicken-nugget incident)

**Architecture:**
- **Multi-channel input** → Channel Adapters → Message Normalization → Agent Core
- **Agent memory** preserves session context across conversations
- Cost optimized: ~$0.006 per order; infrastructure cost ~$88/month
- End-to-end latency: 3-4 seconds
- **60% discount** on infrastructure using Agent Core

**Team Insights:**
- Team had diverse backgrounds and communication challenges (Indian English, American English, Vietnamese)
- Despite challenges, collaboration was effective
- 70% of winning factor: solving a real business problem, not just technical excellence

#### Sign Signal C Team: Dream AI - Competitive Intelligence Platform

**Business Problem:**
- Traditional hackathon ideas (To-Do lists, marketing dashboards) are not compelling to investors
- **Key Insight:** Technology sophistication cannot compensate for lack of business value

**Solution:**
- Platform collecting fragmented signals from competitor companies
- Uses **AWS Bedrock** for foundational models
- **Multi-agent architecture** with A2A (Agent-to-Agent) communication
- **Crawler Subagent**: uses Tiny Fish (for dynamic content) and custom API scraping
- **Analysis Subagent**: evaluates data quality using Langfield for scoring
- Data stored in **S3** and **DynamoDB**
- Natural language interface for non-technical users
- Forecasts ROI, revenue growth, and risks when adopting competitor strategies

**Challenges:**
- Dependency on third-party services (Tiny Fish, Langfield) increased costs significantly ($35 → $94/month)
- Team addressed cost concerns by migrating to native AWS services (WebSocket tools, browser tools)

**Lessons Learned:**
- Clear direction is critical—too many ideas without focus are counterproductive
- Execution matters more than ideas alone
- Teamwork requires ego management and trust
- Start from business problems, not technology

#### Team 3K: Shepher - Smart Queue Management

**Business Problem:**
- Congestion at airports, supermarkets, and event venues
- Long queues cause customer frustration and operational inefficiency

**Solution:**
- AI-powered camera monitoring system using **YOLO V26** (small model for efficiency)
- **ByteTrack** for object tracking and ID assignment
- **AWS Kinesis Video Streams** for video ingestion
- **Fargate clusters** for containerized processing
- **Real-time zone-based tracking** with configurable zones
- **AI agent** with memory to analyze congestion patterns and make recommendations
- Human-in-the-loop design

**Technical Stack:**
- YOLO V26 small model (cost optimization: initial SageMaker with large model cost $48 for 3 hours)
- WebSocket for real-time communication
- AWS infrastructure for secure, scalable deployment

**Team Experience:**
- First hackathon for most members
- Started with "DREAM AI" project, failed, pivoted to Shepher
- Emphasized: **"Code can be learned anytime; experiences like hackathons are unique"**
- Important: Keep scope manageable, don't over-engineer

#### Team Six Pillars: Adaptive Workflow Engine - Anti-Money Laundering (AML)

**Business Problem:**
- Traditional AML systems have 90-95% false positive rates
- $1.58 trillion in suspicious transactions annually
- Manual review processes cost $20-25 per case and take hours
- Data analysts experience burnout from manual processing

**Solution:**
- AI-powered investigation platform reducing traditional 3-hour process to minutes
- **Multiple specialized agents**: KYC Agent, Transaction Agent, Evidence Builder
- **XGBoost** for transaction scoring
- **Three-tier architecture**:
  1. Fast detection layer (XGBoost classifier on AWS Bedrock)
  2. Deep investigation layer (multi-agent orchestration with Step Functions)
  3. Human review layer (case management dashboard)
- **Kinesis Data Streams** for high-volume transaction processing
- **DynamoDB** for alert storage
- **OpenSearch** for vector-based retrieval of legal/topology knowledge
- **Bedrock Guardrails** for output verification and hallucination prevention

**Key Features:**
- Explainability: All agent reasoning is logged for audit
- Scalability: One analyst can handle multiple cases simultaneously
- Human-in-the-loop: Escalation for uncertain cases
- Self-healing: Agents can learn from outcomes

**Enterprise Trust Considerations:**
- **Security**: AWS KMS, IAM, Secret Manager for access control
- **Monitoring**: CloudWatch, X-Ray for observability
- **Human**: Final decision authority remains with human analysts

**Lessons Learned:**
- Define clear scope and out-of-scope boundaries
- 24-hour timeframe requires strict task division
- Maintain calm mindset—focus on learning, not just winning

#### Team BL: Architecture & Cost Estimation Assistant

**Business Problem:**
- SA/Architects receive urgent client requests (2-3 days or same-night delivery)
- Manual architecture diagram creation and cost estimation is time-consuming

**Solution:**
- Natural language interface for architecture generation
- **Upload documents** for custom policies and requirements
- Auto-generate architecture diagrams (Draw.io)
- Integrated cost calculator for AWS services
- **Infrastructure-as-Code (IaC)** generation (CloudFormation, Terraform)
- One-click deployment
- Supports non-technical users and experienced architects

**Key Benefits:**
- Reduces SA effort from days to minutes
- Eliminates manual diagram drawing and cost estimation
- Self-service for non-technical stakeholders
- Automated IaC generation and deployment

### Key Takeaways

#### Business Perspective

- **Start from business problems**, not technology—70% of winning factor is solving a real business need
- **Collaboration beats individual effort**—teams with diverse skills and backgrounds outperform isolated individuals
- **Real-world problem solving** is more valuable than perfect technical execution
- **Networking is critical**—90% of jobs come through referrals, not public job postings
- **Focus on user experience**—remove friction, reduce app switching, maintain natural conversation

#### Technical Perspective

- **Multi-agent architecture** is powerful but requires careful design and cost optimization
- **Cost optimization** is critical—balance model size, third-party dependencies, and infrastructure
- **Human-in-the-loop** is essential for critical systems (AML, security, infrastructure)
- **Memory and context** preservation improves agent effectiveness
- **Observability** (logging, tracing, auditing) is crucial for production systems
- **Open source and third-party tools** offer quick wins but may become cost/security bottlenecks

#### Best Practices

- **Scope management**: Keep projects focused; don't over-engineer
- **Team formation**: Find complementary skills, not identical ones
- **Rapid prototyping**: Build quickly, learn from failures, iterate
- **Documentation**: Diagrams and architecture matter as much as code
- **Security-first thinking**: Especially for financial and critical infrastructure

### Applying to Work

- **Apply multi-agent architectures** to current projects, starting with one simple use case
- **Evaluate cost optimization** strategies—compare model sizes, third-party dependencies, and native cloud services
- **Prototype a conversational interface** for existing applications to reduce user friction
- **Improve observability** in current systems—implement logging, tracing, and auditing
- **Adopt AI guardrails** (like Bedrock Guardrails) to prevent hallucinations in production systems
- **Build side projects** that solve real business problems, not just technical exercises
- **Join hackathons and community events** to build network and gain hands-on experience

### Event Experience

Attending the **FCAJ x Agentic AI Build Week** hackathon was an incredibly valuable experience, giving me a comprehensive view of building AI agents to solve real-world business problems. Key experiences included:

#### Learning from speakers
- Industry experts from AWS shared best practices in AI agent design, cloud architecture, and career development
- Joseph Marazota's opening remarks emphasized that young professionals have a unique advantage—they bring fresh perspectives and aren't burdened by legacy thinking
- The **Capability × Visibility × Consistency = Results** framework was a key takeaway

#### Hands-on team projects
- Participating in team formation, brainstorming, and building AI agents within tight timeframes
- Learning how different teams approached the same problem from diverse angles:
  - One Team focused on conversational ordering (KFC)
  - Sign Signal C built competitive intelligence
  - Team 3K developed smart queue management
  - Six Pillars tackled AML compliance
  - Team BL created architecture estimation tools

#### New technologies explored
- AWS Bedrock for foundational models and guardrails
- Tiny Fish for web scraping and data extraction
- YOLO V26 for real-time computer vision
- Step Functions for orchestrating multi-agent workflows
- OpenSearch for vector-based retrieval
- AWS Kinesis for streaming data processing

#### Networking and discussions
- The hackathon provided opportunities to connect with builders, engineers, and business professionals
- Real-world examples reinforced that **70% of success** comes from solving a real business problem, not just technical excellence
- Teams with diverse backgrounds (Indian, Vietnamese, American) demonstrated the power of global collaboration

#### Lessons learned
- Starting from business problems, not technology, leads to more impactful solutions
- Teamwork requires ego management and trust—clear direction is critical
- Cost optimization is as important as technical capability
- Human-in-the-loop is essential for critical systems
- Speed matters: build quickly, test, learn, and iterate

#### Some event photos
![Speaker presentation](/images/3-Event/Event4/AI_Agent_Build.png)

