---
title: "Event 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.2. </b> "
---


# Summary Report: “Agent Forge Deep Dive Day 1”

### Event Objectives

- Introduction to Amazon Bedrock AgentCore
- Deploy a basic agent in AgentCore
- Connect external tools and Knowledge Bases
- Build a Web UI and integrate Amazon Cognito authentication

### Speakers

- **Nghia Tran** – Agentic SA
- **Anh Pham** – Cloud Consultant, G-AsiaPacific Vietnam


### Key Highlights

#### What is Agentic AI
- (Partially or fully) autonomous software systems that leverage AI to reason, plan, and complete tasks on behalf of humans or systems.

#### Strands Agents
- Strands Agents is an open-source SDK for building agents using just a few lines of code.
- Ease of use: intuitive agent development that gets you started in minutes instead of hours.
- Extensibility: support for custom model providers, custom tools, and MCP.
- Rapid development: quick prototyping and iteration.

#### Amazon Bedrock AgentCore
- The platform to build, connect, and optimize agents — any framework, any model.

- **Ship agents fast**: build and deploy agents without months of infrastructure work.
- **Connect to anything**: give agents secure access to MCP servers, APIs, and knowledge bases.
- **Optimize continuously**: trace every agent decision, evaluate its performance, and safely test improvements in production.
- **AgentCore Runtime**: a secure, serverless runtime environment purpose-built for deploying and scaling dynamic AI agents and tools (e.g. MCP servers), regardless of framework, protocol, or model choice.
- **Identifying the right AI model for an agent**: to choose the right model for the right task, you need to read the documentation.
- **Pricing**: AgentCore is serverless, which helps save cost.

#### Amazon Bedrock AgentCore Identity

- Inbound and outbound auth managed directly from AgentCore.
- **Workload Identities**: the agent's staff badge; issues short-lived Workload Access Tokens (WAT).
- **Credential Providers**: store how to authenticate to a service — API key, or OAuth client_id + secret.
- **Token Vault**: encrypted store (Secrets Manager + KMS); caches tokens keyed per user.
- **Broker Logic**: performs OAuth server-side — M2M, 3LO, OBO — and returns a finished token.

#### Amazon Bedrock AgentCore Gateway

- **How do we scale?**: we create a gateway as middleware that helps manage the connection between agents and APIs/tools/resources.
- **Secure access**: AgentCore Gateway can save logs to Amazon CloudWatch.
- **Sync vs async comparison**: understanding the trade-offs.
- **AgentCore Semantic Search**: AgentCore Gateway automatically indexes tools and provides serverless semantic search. It reduces the context passed to the agent's LLM, improving accuracy, speed, and cost, and lets the agent focus on the tools relevant to a given task. The search tool name is x-amz-bedrock-agentcore-search.



### Event Experience

Attending the **“Agent Forge Deep Dive Day 1”** workshop was extremely valuable, giving me a comprehensive view of building and operating AI agents using advanced methods and tools. Key experiences included:


#### Hands-on technical exposure
- Learned the fundamentals of **Amazon Bedrock AgentCore** and its capabilities — **Runtime, Gateway, Identity** — to understand the service used throughout the workshop.
- Participating in the **hands-on workshop** sessions helped me build a local web app and create my own AI agent with Kiro.


#### Leveraging modern tools
- Explored **Amazon Bedrock AgentCore**, an agentic platform for building, deploying, and operating highly effective agents securely at scale using any framework and foundation model.


#### Some event photos
![Overall definition of an Agent](/images/4-Event/aws_event_agentcore_1.jpg)

![A gradient of autonomy](/images/4-Event/aws_event_agentcore_2.jpg)

> Overall, the interactive hands-on workshop provided by the event gave me insight into new technical knowledge and sparked new ideas for future personal projects.
