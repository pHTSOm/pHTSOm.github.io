---
title: "Week 10 Worklog"
date: 2026-02-04
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---

### Week 10 Objectives:

Move the whole infrastructure into code. Rebuilt what had been configured in the console as modular Terraform — auth, API, compute, and data modules — and set up a remote state backend on S3 with DynamoDB locking so my teammate and I can work on the same infrastructure safely.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Design the Terraform project layout as reusable modules: `auth/`, `api/`, `compute/`, `data/`                                                                                   | 06/22/2026 | 06/22/2026      | <https://developer.hashicorp.com/terraform/language/modules> |
| 3   | - Write the `auth` module (Cognito User Pool, app client, Hosted UI domain) and the `api` module (REST API, routes, Cognito authorizer, usage plan)                                              | 06/23/2026 | 06/23/2026      | <https://registry.terraform.io/providers/hashicorp/aws/latest/docs> |
| 4   | - Write the `compute` module (Lambda function packaging, environment variables, least-privilege IAM role) and the `data` module (DynamoDB table) | 06/24/2026 | 06/24/2026      | <https://registry.terraform.io/providers/hashicorp/aws/latest/docs> |
| 5   | - Configure the remote state backend: S3 bucket for state and DynamoDB table for state locking                            | 06/25/2026 | 06/25/2026      | <https://developer.hashicorp.com/terraform/language/backend/s3> |
| 6   | - Run `terraform plan` / `apply` to verify the whole stack is reproducible from code <br> - Clean up the repo (`.terraform` provider binaries ignored)                                                                                     | 06/26/2026 | 06/26/2026      |  |


### Week 10 Achievements:

* Restructured the entire infrastructure as modular Terraform instead of hand-configured console resources, split into `auth/`, `api/`, `compute/`, and `data/` modules.
* Codified the full Cognito + API Gateway integration in Terraform, including the authorizer, Lambda proxy integration, usage plan, and API key.
* Wrote a least-privilege IAM role for the Lambda in the compute module, granting only the specific DynamoDB and Bedrock actions it needs.
* Set up remote Terraform state on S3 with a DynamoDB lock table, so two people can work against the same infrastructure without state conflicts or corruption.
* Verified the stack is fully reproducible: `terraform plan` shows a clean diff and `apply` recreates the environment from code alone.

