---
title: "Week 11 Worklog"
date: 2026-02-04
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---

### Week 11 Objectives:

Build the CI/CD pipeline and add observability to the backend. Connected the GitHub repository to AWS CodePipeline, wrote the buildspec automation (tests, security scans, Terraform plan), instrumented the Lambda with custom latency metrics, and built a CloudWatch dashboard with SNS alerting — then pushed a real change end-to-end through the pipeline and fixed what the security scanner caught.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Provision AWS CodePipeline and a CodeStar connection to the GitHub repository <br> - Resolve the connection stuck in "Pending" by authorizing the GitHub connection manually in the AWS console                                                                                   | 06/29/2026 | 06/29/2026      | <https://docs.aws.amazon.com/codepipeline/latest/userguide/connections-github.html> |
| 3   | - Write `buildspec-test.yml` to run pytest, bandit, and tfsec plus `terraform plan` on every push <br> - Fix the build failing because the CodeBuild image's pre-installed Terraform didn't match, removed it and pinned an exact Terraform version installed in the `install` phase                                              | 06/30/2026 | 06/30/2026      | <https://docs.aws.amazon.com/codebuild/latest/userguide/build-spec-ref.html> |
| 4   | - Instrument the Lambda to measure Bedrock call latency and publish it as custom CloudWatch metrics (`Custom/Bedrock` namespace) <br> - Add `cloudwatch:PutMetricData` to the Lambda's IAM policy in the Terraform compute module so the metrics can publish | 07/01/2026 | 07/01/2026      | <https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/publishingMetrics.html> |
| 5   | - Build a CloudWatch dashboard showing Lambda duration and Bedrock latency percentiles (p50/p95/p99) <br> - Create an error alarm wired to an SNS email topic, scoped to server-side 5XX errors over a consecutive 5-minute window so client-side 4XX test requests don't page                            | 07/02/2026 | 07/02/2026      | <https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch_Dashboards.html> |
| 6   | - Push a change end-to-end through the pipeline <br> - Fix the tfsec findings that blocked the security stage: scoped the IAM logs permission to the specific log group, enabled DynamoDB server-side encryption + point-in-time recovery, and added justified inline ignores for accepted findings                                                                                     | 07/03/2026 | 07/03/2026      | <https://aquasecurity.github.io/tfsec/> |


### Week 11 Achievements:

* Stood up a working CI/CD pipeline: GitHub push → CodeBuild test stage (pytest, bandit, tfsec, `terraform plan`) → manual approval → `terraform apply`.
* Learned that a CodeStar GitHub connection stays "Pending" until it is authorized once by hand in the console — infrastructure-as-code can provision it, but the OAuth handshake is inherently manual.
* Debugged the CodeBuild environment by controlling the toolchain myself: the buildspec now removes the image's pre-installed Terraform and installs a pinned version, so builds are reproducible.
* Instrumented the Lambda with custom Bedrock latency and success/error metrics in the `Custom/Bedrock` namespace, and learned metrics silently fail to appear without `cloudwatch:PutMetricData` in the execution role.
* Built a CloudWatch dashboard charting Lambda duration and Bedrock latency at p50/p95/p99, plus API Gateway and DynamoDB panels.
* Tuned alarming to be meaningful: the SNS email alarm only fires on 5XX server errors sustained over consecutive 5-minute evaluation periods, so intentional bad requests during manual testing (4XX) don't trigger false pages.
* Experienced the security gate working as intended: tfsec blocked the pipeline until IAM permissions were scoped down and DynamoDB encryption/PITR were enabled — and learned that ignore comments must be placed at the resource level to be honored.
