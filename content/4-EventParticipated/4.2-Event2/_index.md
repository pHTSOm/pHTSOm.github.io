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
- Deploy a basic agent is AgentCore
- Connect external tools and Knowledge Bases
- Build a Web UI annd integrate Amazon Cognito authentication

### Speakers

- **Nghia Tran** – Agentic SA
- **Anh Pham** – Cloud Consultant G-AsiaPacific Vietnam


### Key Highlights

#### What is Agentic AI
- (Partially/fully) Autonomous software sytems that leverage AI to reason, plan, and complete tasks on behalf of humanns or system

#### Strands agents
- Strands Agents is an open source SDK for building agents using just a few line of code
- Ease of use: Intuitive agent development to get started inn minutes instead of hours  
- Extensibility: Support for custom model providers, custom tools, and MCP  
- Rapid development: Quick prototyping and iteration.  

#### Amazon Bedrock AgentCore
- The platform to build, connect, and optimize agents. Any framework, any model

- **Ship Agents Fast**: Build and deploy agents without months of infrastructure work  
- **Connect to anything**: Give agents secure access to MCP servers, APIs, and knowledge bases  
- **Optimize continuously**: Trace every agent decision, evaluate its performance, and safely test improvements in production  
- **AgentCore Runtime**: is a secure, serverless runtime environment purpose-built for deploying and scaling dynamic AI agents and tools(e.g. MCP servers), regardless of framework, protocol, or model choice
- **To identify a right AI model for Agent**: To choose a right model for right word, must read documents.
- **Pricing**: AgentCore using serverless which help save money.

#### Amazon Bedrock agenntcore Identity

- Inbound auth and outbound auth manage directly from AgentCore
- **Workload Identities**: The agent's staff badge; issues short-lived Workload Access Tokens(WAT)  
- **Credential Providers**: Stores how to auth to one service - API key or OAuth client_id + secret.
- **Token Vault**: Encrypted store (Secrets Mgr + KMS); caches tokens keyed per user
- **Broker Logic**: Performs OAuth server-side - M2m, 3LO, OBO - returns a finish token

#### Amazon Bedrock AgentCore Gateway

- **How do we scale**: We will create a gateway as a middleware which help manage the connnection between agents and APIs/Tools/Resources  
- **AgentCore Gateway Provide secure access**: AgentCore Gateway can save log to Amazon CloudWatch.
- **Sync vs async comparison**: Understanding the trade-offs.
- **AgentCore Semantic Search**: AgentCore Gateway automatically indexes tools, and gives serverless semantic search. reduces context passed to agent's LLM, improving accuracy, speed, and cost. Lets agent focus on tools relevant for a given task. The search tool name is x-amz-bedrock-agentcore-search  



### Event Experience

Attending the **“Agent Forge Deep Dive Day 1”** workshop was extremely valuable, giving me a comprehensive view of modernizing applications and databases using advanced methods and tools. Key experiences included:


#### Hands-on technical exposure
- Learned about the fundamental of **Amazon Bedrock AgentCore** and its functions **Runtime, Gateway, Identity** to get to know about the service for the workshop.  
- Participating in **Workshop-hands-on** sessions helped me to create a web-local and create my own AI agent with Kiro.  


#### Leveraging modern tools
- Explored **Amazon Bedrock AgentCore**, an agentic platform for building, deploying, and operating highly effective agents securely at scale using any framework and foundation model.  


#### Some event photos
![Overall definition of an Agent](/images/4-Event/aws_event_agentcore_1.jpg)  

![A gradient of autonomy](/images/4-Event/aws_event_agentcore_2.jpg)  

> Overall, through interactive hands-on workshop provided by the event help me have insight of new technical knowledge. Help me have a new idea for future self project.
