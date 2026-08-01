---
title: "Week 8 Worklog"
date: 2026-02-04
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives:

Build the core backend logic of the summarizer: calling Amazon Nova Lite through Bedrock, extracting the summary from the model response, persisting results to DynamoDB, hardening the Bedrock call with retry logic, and covering the database logic with unit tests.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Write the base Python function using `boto3.client('bedrock-runtime')` to call Nova Lite <br> - Debug request body validation errors by printing the exact payload and comparing it against the Nova model documentation                                                                                   | 06/08/2026 | 06/08/2026      | <https://docs.aws.amazon.com/bedrock/latest/userguide/> |
| 3   | - Write the logic to pull the summary text out of the model's response object                                              | 06/09/2026 | 06/09/2026      | <https://docs.aws.amazon.com/bedrock/latest/userguide/> |
| 4   | - Write the DynamoDB persistence logic to save the input text and AI summary into the table | 06/10/2026 | 06/10/2026      | <https://boto3.amazonaws.com/v1/documentation/api/latest/guide/dynamodb.html> |
| 5   | - Add retry handling with exponential backoff around the Bedrock call for transient errors                            | 06/11/2026 | 06/11/2026      |  |
| 6   | - Write unit tests for the database logic using pytest and moto                                                                                     | 06/12/2026 | 06/12/2026      | <https://docs.getmoto.org/> |


### Week 8 Achievements:

* Implemented the core summarization function calling Amazon Nova Lite via the `bedrock-runtime` boto3 client.
* Debugged Bedrock request validation errors by printing the exact payload sent and comparing it field-by-field against the Nova model documentation until the request body structure matched and the call succeeded.
* Wrote the response-parsing logic that extracts the summary text from the nested model response object.
* Implemented the DynamoDB write path storing `user_id`, `timestamp`, the original text, and the generated summary.
* Made the API more stable under repeated requests by adding retry handling with exponential backoff around the Bedrock call for transient throttling/timeout errors.
* Wrote unit tests for the database logic using pytest with moto to mock DynamoDB, keeping tests independent of real AWS resources.
