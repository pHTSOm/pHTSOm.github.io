---
title: "Week 12 Worklog"
date: 2026-02-04
weight: 2
chapter: false
pre: " <b> 1.12. </b> "
---

### Week 12 Objectives:

The final week: harden the account against the CIS AWS Foundations Benchmark, load-test the API with Locust, clean up repository and infrastructure loose ends, deploy the static frontend to S3 + CloudFront.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Enable multi-region AWS CloudTrail and AWS Config with a CIS AWS Foundations Benchmark conformance pack <br> - Fix the CloudTrail → CloudWatch Logs integration failing because the log group ARN requires an explicit `:*` suffix                                                                                   | 07/06/2026 | 07/06/2026      | <https://docs.aws.amazon.com/config/latest/developerguide/operational-best-practices-for-cis_aws_benchmark_level_1.html> |
| 3   | - Run the Locust load test against the API with 50 concurrent users hammering POST /summarize <br> - Investigate the flood of 429 responses: the API Gateway usage plan throttle (2 req/s) was rejecting traffic exactly as designed — verified on the CloudWatch dashboard that the backend stayed healthy behind the throttle                                              | 07/07/2026 | 07/07/2026      | <https://docs.locust.io/> |
| 4   | - Write the frontend Terraform module (S3 bucket + CloudFront distribution) and deploy the static frontend <br> - Fix the login button breaking on the live site because Cognito still redirected to localhost, added the CloudFront domain to the Cognito callback URLs in the Terraform auth module | 07/08/2026 | 07/08/2026      | <https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/> |
| 5   | - Clean up files wrongly tracked in git (`.env` files, `.DS_Store`, `__pycache__` artifacts) <br> - Learn that `.gitignore` does not affect already-tracked files — they must be removed from the index with `git rm --cached` first                            | 07/09/2026 | 07/09/2026      |  |
| 6   | - Rewrite the README to accurately reflect the implemented architecture, removing claims about features that were never built                                                                             | 07/10/2026 | 07/10/2026      |  |


### Week 12 Achievements:

* Deployed multi-region CloudTrail, AWS Config, and the CIS AWS Foundations Benchmark conformance pack, and debugged a subtle integration failure: CloudTrail's CloudWatch Logs role needs the log group ARN with an explicit `:*` suffix.
* Load-tested the API with Locust at 50 concurrent users and interpreted the results correctly: the 429 responses were the usage plan's 2 req/s throttle protecting the backend, not a failure — the CloudWatch dashboard confirmed no 5XX errors or Lambda failures behind the throttle. (Bedrock responses were served through the mock summarize path, since the account's Bedrock on-demand quota increase was still pending with AWS Support.)
* Shipped the last missing piece of infrastructure: a frontend Terraform module hosting the static site on S3 behind CloudFront, and fixed the live login flow by adding the CloudFront domain to Cognito's callback URLs alongside `localhost`.
* Cleaned the repository of secrets-adjacent and generated files (`.env`, `.DS_Store`, `__pycache__`), learning that `.gitignore` only prevents *new* files from being tracked — existing ones need `git rm --cached`.
* Rewrote the README so the documentation matches what is actually deployed — removing leftover claims about caching and rate limits that were never implemented — and prepared a demo walkthrough covering a clean pipeline run, the full auth flow, the summarize/history API, and the live metrics dashboard.
* Final state of the platform: fully reproducible from Terraform, security-scanned on every push, monitored with dashboards and alarms, CIS-benchmarked, load-tested, and live on CloudFront.
