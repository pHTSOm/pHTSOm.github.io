---
title: "Week 6 Worklog"
date: 2026-02-04
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives:

Kicked off the graduation project (an AI-powered document summarization platform on AWS). This week was about planning before building: finalizing the project proposal, designing the serverless architecture, selecting the right AWS services within a student budget, and agreeing on the division of work with my teammate.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Draft and finalize the project proposal for the Automated Document Summarizer platform                                                                                   | 05/25/2026 | 05/25/2026      |  
| 3   | - Design the serverless architecture: <br>&emsp; + Cognito <br>&emsp; + API Gateway <br>&emsp; + Lambda <br>&emsp; + DynamoDB <br>&emsp; + Amazon Bedrock <br> <br> - Draw the architecture diagram                                              | 05/26/2026 | 05/26/2026      | <https://docs.aws.amazon.com/serverless/> |
| 4   | - Compare Amazon Bedrock foundation models on capability and pricing <br> - Selected Amazon Nova Lite as the summarization model | 05/27/2026 | 05/27/2026      | <https://docs.aws.amazon.com/bedrock/> |
| 5   | - Agree on division of work with teammate (backend + infrastructure vs. frontend + weekly report feature)                            | 05/28/2026 | 05/28/2026      |  |
| 6   | - Break the project into phases and write the implementation checklist                                                                                     | 05/29/2026 | 05/29/2026      |  |


### Week 6 Achievements:

* Finalized the project proposal for an AI document summarization backend on AWS.
* Designed a fully serverless architecture: Cognito for authentication, API Gateway as the entry point, Lambda for compute, DynamoDB for storage, and Amazon Bedrock for the AI summarization itself.
* Compared Bedrock model options and chose Amazon Nova Lite as the best capability/price fit for a student-budget project.
* Learned to evaluate services through a cost lens first. Chose on-demand DynamoDB and serverless components specifically to stay inside a small monthly budget ceiling.
* Split responsibilities clearly with my teammate: I own the backend, Bedrock integration, and infrastructure.
* Produced a phased implementation checklist that the following weeks' work would follow.
