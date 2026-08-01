---
title: "Week 7 Worklog"
date: 2026-02-04
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives:

Set up the full development environment for the project: AWS CLI and Terraform tooling, the shared Git repository with branch rules, and the foundational research needed before writing the backend. Bedrock pricing and limits, the Lambda invocation model, and DynamoDB key design.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Install AWS CLI and Terraform <br> - Fix `aws sts get-caller-identity` returning "unable to locate credentials" <br> - Review AWS documentation on least-privilege IAM policies                                                                                   | 06/01/2026 | 06/01/2026      | <https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html> |
| 3   | - Set up the shared repository and add branch protection rules on `main` <br> - Agree with teammate on a branching convention and commit message style                                              | 06/02/2026 | 06/02/2026      |  |
| 4   | - Read Bedrock's pricing page and Nova Lite's model documentation to understand token limits, pricing per request, and realistic input sizes | 06/03/2026 | 06/03/2026      | <https://docs.aws.amazon.com/bedrock/> |
| 5   | - Read Lambda documentation on handler structure and invocation <br> - Study the Lambda proxy integration format and fix the handler to read from `event['body']` instead of the raw event <br> - Test sample event payloads in the Lambda console                            | 06/04/2026 | 06/04/2026      | <https://docs.aws.amazon.com/apigateway/latest/developerguide/set-up-lambda-proxy-integrations.html> |
| 6   | - Study DynamoDB partition key and sort key design <br> - Finalize the NoSQL data structure for the summarizer table                                                                                     | 06/05/2026 | 06/05/2026      | <https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/best-practices.html> |


### Week 7 Achievements:

* Installed and configured AWS CLI and Terraform, and debugged a credentials issue where `aws sts get-caller-identity` could not locate credentials until the profile was configured correctly.
* Reviewed AWS's guidance on least-privilege IAM policies to apply from the start of the project.
* Set up the shared repository with branch protection on `main`, and agreed a branching convention and commit message style with my teammate so we don't step on each other's work.
* Understood Bedrock's pricing model and Nova Lite's token limits well enough to define a realistic maximum input size for the summarizer.
* Learned how API Gateway's Lambda proxy integration wraps requests 
    * The handler must parse `event['body']` rather than treating the raw event as the payload  
    * Verified this with test events in the Lambda console.
* Finalized the DynamoDB table design: `user_id` as partition key and `timestamp` as sort key, storing the original text and its AI summary.
