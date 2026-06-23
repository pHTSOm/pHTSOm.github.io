---
title: "Week 6 Worklog"
date: 2026-02-04
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---


### Week 6 Objectives:

* Select tech stack for the project.
* Design a single-table DynamoDB schema with composite keys.
* Validate Bedrock prompts with temperature control for consistency.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Planning and choosing topic for the project <br>  - Pick the backend tech stack                                                                                                   | 05/18/2026 | 05/18/2026      |
| 3   | - Sketch out how data moves through the app                                              | 05/19/2026 | 05/19/2026      | <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03/> |
| 4   | - Pick the AI model and see how it handles text | 05/20/2026 | 05/20/2026      | <https://docs.aws.amazon.com/bedrock/latest/userguide/what-is-bedrock.html> |
| 5   | - Figure out how to do the automated CSV export                            | 05/22/2026 | 05/22/2026      | 
| 6   | - Create a checklist for security and testing                                                                                     | 05/22/2026 | 05/22/2026      | 


### Week 6 Achievements:

* I was worried about Lambda cold starts may messing up the synchronous response time for long texts but after a session of talking with my friend and a little bit of research I realized that the simplicity of Lambda outweighs the pain of managing an ECS cluster.

* I designed a single table DynamoDB schema using a composite key of user_id and timestamp to enable efficient, sorted history retrieval without complex relational joins.

* I try to using and testing the AI model in summarize text and the output sometimes it gave a paragraph, sometimes a bulleted list, and found out that I can explicitly telling the model to "summarize in exactly 3-4 sentences" and locking the temperature to a low 0.2 keeps it deterministic.

* I looked up how EventBridge cron jobs trigger Lambda functions to run background tasks

* I researched how to build a basic AWS CodePipeline and what tools we need to scan our code for security issues.
