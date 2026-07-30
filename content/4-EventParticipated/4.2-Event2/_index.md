---
title: "Event 2"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---


### Event Objectives

- Showcase real-world AI agent applications across multiple domains
- Provide hands-on technical insights from industry practitioners
- Foster community learning and networking
- Demonstrate AWS services in production (Amazon Q, Bedrock, DevOps Agent, Voice AI)
- Highlight the intersection of AI, business, and enterprise needs

### Speakers

- **Steve Trần** – Founder, Cloud Thinker
- **Hiếu Nghị** – Renova Cloud (Voice AI Session)
- **Kiệt** – Student Builder (Voice AI Demo)
- **Trung** – Founder & CEO, R AI
- **Bảo** – Cloud Engineer, Cloud Kinetics (DevOps Agent)
- **Nguyên** – Cloud Engineer, Cloud Kinetics (DevOps Agent)
- **Trường** – AI Solution Architect, Noventis (Amazon Q & HR)
- **Minh Anh** – Solution Architect, Noventis (Amazon Q & HR)
- **Toàn Nguyễn** – AWS Security Builder (Amazon Q Security)
- **Nghị** – Renova Cloud (Amazon Q Security)

### Key Highlights

#### Session 1: Cloud Operations & AI (Steve Trần – Cloud Thinker)

**Career Journey & Market Insights:**
- Started in IT during COVID era; cloud demand was explosive
- Recognized cloud as a high-growth market early and pivoted
- AI is shifting demand from junior developers to senior engineers who can effectively use AI tools
- Current enterprise challenge: **complexity** – legacy systems, multi-cloud, and lack of DevOps talent

**Cloud Thinker's Platform:**
- Solves operational pain points using **agentic AI**:
  - **Incident Management**: AI investigates root causes minutes vs. hours
  - **Quality Control**: AI reviews infrastructure changes before production to reduce defects
  - **Cost Optimization**: AI continuously monitors and suggests optimizations – many clients have shifted FinOps tasks to AI
  - **Security**: Built-in penetration testing and compliance assessment

**Key Architectural Decisions:**
- **Multi-agent vs. Single Agent**: Debate between specialist agents and a single super-agent
  - Multi-agent allows for more focused contexts, better cost control, and role-based access
  - Single agent can do 95% of tasks, but with higher costs and hallucination risks
  - Cloud Thinker uses **multi-agent architecture** for better handling of enterprise complexity

**Challenges for Startups:**
- Selling to enterprises requires changing 50% of their processes
- Need **champion customers** (e.g., F88, FPT) to validate product-market fit
- Build a **fully managed service** to educate and support enterprise transitions
- Expect to spend 10x more effort on enterprise onboarding than on SaaS delivery

**Takeaway:** Focus on real problems; work fast, iterate, and find customers early.

#### Session 2: Voice AI – Enabling Vietnamese Speech Agents (Hiếu Nghị, Kiệt, Trung)

**Voice AI Landscape:**
- Speech-to-speech models are mostly English-only – Vietnamese is a **low-resource language**
- Current approach in Vietnam: **STT → LLM → TTS** pipeline (separate components)
- This enables control, tool calling, and Vietnamese language support

**Components:**
- **STT (Speech-to-Text)**: Convert voice to text – custom-trained for Vietnamese accents
- **LLM**: Handles reasoning, context, tool calling – works well with Vietnamese
- **TTS (Text-to-Speech)**: Convert response back to voice – can be customized for different accents/use cases

**Challenges for Vietnamese Voice AI:**
- **Accent handling**: Training data includes 10-20% regional accents (Northern, Central, Southern)
- **Gender detection**: Vietnamese requires proper pronoun usage (anh/chị) – models must detect speaker gender
- **Interruption handling**: Models must decide when to speak and when to listen – requires additional training
- **Latency**: End-to-end streaming is critical for natural conversation

**Enterprise Features:**
- **Self-service prompt management** for business users (non-technical)
- **Versioning and audit logs** for compliance (like GitHub)
- **Knowledge base** integration for domain-specific answers
- **Human handoff**: Seamless transfer from AI to human when AI cannot handle the query
- **Voice personalization**: Use case-specific voices (e.g., debt collection may use regional accent for better engagement)

**Live Demo:**
- Quick Agent built on **AWS Bedrock** with **Knowledge Base** for Apple product support
- Answered questions about MacBook Pro – speech-to-speech in English (later clarified that Vietnamese support is under development)

**Takeaway:** Voice AI in Vietnamese is a growing field; focus on the pipeline approach for control and reliability.

#### Session 3: DevOps Agent – Intelligent Incident Management (Bảo & Nguyên – Cloud Kinetics)

**Problem Statement:**
- Manual troubleshooting is fragmented: logs in multiple places, knowledge silos, constant interruptions
- MTTR (Mean Time to Resolution) is too high due to lack of context

**Solution – AWS DevOps Agent (Amazon DevOps Guru? but they called it "DevOps Agent" or "DevOps AI Agent" – actually it's a new service, likely Amazon DevOps Guru or a similar agent)**

**Six Core Capabilities:**
1. **Context Learning**: Agent builds a topology of your entire infrastructure (AWS, on-prem, Azure) – learns relationships and dependencies
2. **Control**: Full RBAC – agent can be restricted to specific resources via tags and IAM policies
3. **Integration**: Extensible via MCP (Model Context Protocol) – connect to any data source (logs, databases, custom tools)
4. **Collaboration**: Users can chat, get recommendations, and escalate to ticketing systems (ServiceNow, Slack)
5. **Convenience**: One-click setup via AWS Console; web-based chat interface
6. **Cost-Effective**: Priced per second ($0.083/second), not per token – predictable billing

**How It Works (4 Steps):**
1. **Trigger**: Alert (CloudWatch) or user-initiated investigation
2. **Investigation**: Agent analyzes logs, metrics, traces, and topology to generate hypotheses
3. **Mitigation**: Suggests remediation steps (not auto-executes – safety first)
4. **Improvement**: Proposes long-term fixes (e.g., add caching, scale resources)

**Live Demo:**
- Simulated DDoS attack on an e-commerce app (ECS + ALB)
- Agent detected high latency, investigated, identified 10 ECS tasks generating 1000 req/sec, and provided a mitigation plan (stop tasks, scale down)
- Agent also generated a root cause analysis with actionable commands (copy-paste into terminal)
- After applying fixes, app returned to normal

**Success Metrics (from customer cases):**
- University (200k students): Reduced MTTR from 2 hours to 28 minutes (-77%)
- Zenchef (restaurant platform): Found misconfiguration in 20 minutes (-75% vs manual)
- KDDI (Japanese telecom): Reduced investigation from weeks to days

**Prerequisites for Success:**
- Good observability: comprehensive logs, metrics, and alarms
- Large-scale systems: more value in complex environments
- Human-in-the-loop: agent recommends, human executes

**Takeaway:** DevOps Agent is a force multiplier for SRE/DevOps teams; it doesn't replace skills but amplifies them.

#### Session 4: Amazon Q – AI for HR and Talent Management (Trường & Minh Anh – Noventis)

**HR Pain Points in the AI Era:**
- Manual CV screening is time-consuming and error-prone – often misses key talent
- No standardized framework for evaluating candidates across roles
- Data privacy concerns when using public AI tools (exposure of sensitive HR data)
- High cost of wrong hiring: delays, low team performance, employee churn

**Amazon Q – An Agentic AI Assistant:**
- **Customizable Agents**: Build skills for specific tasks (e.g., Talent Review Assistant)
- **Multi-source Research**: Queries internal documents, websites, and structured data
- **Automated Business Intelligence**: Natural language queries over datasets – no SQL needed
- **Flow Automation**: Automate repetitive workflows (email, scheduling, approvals)

**Data Integration:**
- Connects to Microsoft (SharePoint, Outlook, OneDrive) and Google Workspace (Gmail, Drive)
- Can connect to any system via custom MCP connectors
- Data stays in AWS – secure, compliant (already has local zone in Vietnam)

**HR Use Case Demo:**
1. **Create Skill**: Upload an MD file describing the HR talent review process – Q builds a skill automatically
2. **Generate Job Description**: Ask Q to create a JD for "Junior Cloud Engineer" – it generates a complete JD
3. **Screen CVs**: Upload a folder of CVs; Q ranks candidates against the JD with scores (Strong, Good, Low, Very Low)
4. **Generate Report**: Q creates a visual dashboard showing candidate scores, strengths, and recommendations
5. **Action**: Q can send emails, schedule interviews, and update tracking systems via automation

**Results:**
- Reduced screening time from days to minutes
- Standardized evaluation across all candidates
- Enabled HR to focus on strategic decisions

**Security Integration (Toàn & Nghị session):**
- **Private connectivity**: Use **VPC Interface Endpoint** for Amazon Q to connect to MCP servers without exposing them to the internet
- **Benefits**: No public IP, no risk of MITM attacks, data stays within VPC, meets compliance (e.g., data residency)
- **Cost estimate**: ~$250–350/month for private setup (includes Route53 Resolver, ALB, EC2, data transfer)

**Takeaway:** Amazon Q democratizes AI for non-technical teams – HR, Finance, and Operations can now use AI securely and effectively.

### Key Takeaways

#### Business Perspective

- AI is not about replacing human judgment but amplifying it – especially in critical domains (HR, security, operations)
- Enterprises prioritize **security**, **compliance**, and **control** – private connectivity and data residency are non-negotiable
- **Low-code/No-code** AI assistants (like Amazon Q) empower business users to leverage AI without deep technical skills
- **Time-to-value** is critical – tools that reduce manual effort (CV screening, incident investigation) deliver immediate ROI

#### Technical Perspective

- **Multi-agent architectures** are preferred for enterprise complexity due to control, cost, and domain specialization
- **Vietnamese voice AI** requires a pipeline approach (STT → LLM → TTS) because end-to-end models don't support low-resource languages
- **MCP (Model Context Protocol)** is a key enabler for integrating AI with external systems – essential for enterprise adoption
- **Private connectivity** is a must for production-grade AI services – avoid exposing internal APIs to the public internet
- **Streaming** is critical for real-time interaction – both for voice and chat applications

#### Best Practices

- **Start small** – build an MVP that solves a real pain point, then iterate based on feedback
- **Design for human-in-the-loop** – especially in critical systems (AML, security, infrastructure)
- **Invest in observability** – AI agents are only as good as the data they can access
- **Choose the right architecture** – single vs. multi-agent depends on your specific use case and cost constraints
- **Prioritize security from day one** – data governance and access control should be baked in, not added later

### Applying to Work

- **Evaluate multi-agent architectures** for your current project – compare cost, complexity, and flexibility vs. a single agent
- **Prototype a voice agent** using the STT → LLM → TTS pipeline – start with English or existing Vietnamese models
- **Experiment with Amazon Q** – try the free tier to automate a small workflow (e.g., summarizing emails, generating reports)
- **Improve observability** in your systems – ensure logs, metrics, and traces are available for AI agents to consume
- **Implement private connectivity** if you're developing AI services for internal use – avoid exposing APIs to the internet
- **Adopt MCP** to connect AI agents to your existing systems (databases, ticketing, HR systems)

### Event Experience

Attending the **FCAJ Community Day - June 2026** was a comprehensive deep-dive into how AI agents are transforming enterprise operations. Key experiences included:

#### Learning from diverse speakers
- Steve Trần shared the journey from developer to founder, emphasizing the importance of solving real problems and finding champion customers
- The Voice AI session highlighted the unique challenges of Vietnamese language and the practical pipeline approach
- The DevOps Agent demo showed how AI can significantly reduce incident resolution time – a tangible business benefit
- The Amazon Q session demonstrated that AI is not just for engineers; HR and business teams can leverage it too

#### Hands-on technical exposure
- Understanding the trade-offs between multi-agent and single-agent architectures
- Learning about MCP and how to integrate AI with external APIs
- Seeing live demos of AI agents in action – from incident investigation to CV screening
- Discovering the importance of private connectivity for enterprise security

#### New technologies explored
- **AWS Bedrock** (foundational models, guardrails)
- **Amazon Q** (agentic AI assistant for business users)
- **DevOps Agent** (incident management)
- **MCP (Model Context Protocol)** for AI integration
- **Voice AI** (STT, LLM, TTS) for Vietnamese

#### Networking and discussions
- Engaging with speakers and fellow attendees during Q&A sessions
- Learning about real-world challenges and solutions from different industries (banking, retail, telecom)
- Understanding that AI adoption varies by industry – some are more advanced, others are just starting

#### Lessons learned
- **AI is a force multiplier**, not a replacement – it amplifies the skills of those who use it well
- **Security and compliance** are critical for enterprise adoption – private connectivity and data residency are must-haves
- **Multi-agent architectures** offer better control and cost optimization than single-agent systems
- **Building AI products** for enterprises requires patience and close collaboration with customers

#### Some event photos
![Speaker presentation](/images/3-Event/Event3/event3.png)


