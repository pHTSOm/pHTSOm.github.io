---
title: "Self-Assessment"
date: 2026-02-04
weight: 6
chapter: false
pre: " <b> 6. </b> "
---

During my internship with the **First Cloud Journey (FCJ)** program from **April 2026** to **July 2026**, I had the opportunity to move from classroom knowledge to building and operating a real cloud system. After five weeks of structured AWS study, I spent seven weeks building my graduation project — an AI-powered serverless document summarization platform — where I owned the backend, the Amazon Bedrock integration, and the entire infrastructure: Terraform, the CI/CD pipeline, monitoring, and security hardening.

To reflect objectively on this period, I evaluate myself against the following criteria:

| No. | Criteria | Rating | Comment |
| --- | --- | --- | --- |
| 1 | **Knowledge** | Fair | I started with mostly theoretical knowledge and finished able to design and operate a full serverless stack (Lambda, API Gateway, Cognito, DynamoDB, Bedrock, Terraform). There are still gaps — some CIS Benchmark findings on the account remain unresolved, and several services I used for the first time during this project. |
| 2 | **Ability to learn** | Good | Absorbed a large amount of new material quickly: five weeks of foundational study, then roughly ten new AWS services applied in practice. I learned mainly from official documentation and from errors themselves — debugging Bedrock request payloads, tfsec findings, and CodeBuild environment issues against the docs. |
| 3 | **Proactiveness** | Good | When the new account's Bedrock on-demand quota blocked real model calls, I opened an AWS Support case myself and built a mock summarize path so development, testing, and the demo were never blocked. I also went beyond the minimum scope with CI/CD, custom metrics, dashboards, and CIS compliance. |
| 4 | **Discipline** | Fair | I maintained steady working hours, followed the team's branch-protection/PR workflow, and never pushed unreviewed changes to main. However, I fell behind on writing up my worklog entries in real time and had to catch up near the end — something to fix in future projects. |
| 5 | **Communication** | Fair | Coordinated consistently with my teammate on shared resources (Cognito callback URLs, CORS, state) so we never silently broke each other's work. Presenting is still a weak point — condensing seven weeks of infrastructure work into a clear five-minute demo took me multiple attempts. |
| 6 | **Teamwork** | Good | Our two-person split (backend/infrastructure vs. frontend/reporting/load-testing) had clear ownership boundaries, and we integrated through PRs on a protected main branch. Handoffs — like connecting the finished frontend to the real API — went smoothly. |
| 7 | **Problem-solving** | Good | Solved problems systematically rather than by trial-and-error: printing exact request payloads against documentation, tracing a CloudTrail failure to a missing `:*` ARN suffix, recognizing load-test 429s as the usage plan working as designed, and using `git rm --cached` for tracked-file cleanup. |
| 8 | **Contribution to the project** | Good | Owned and delivered the majority of the platform: the summarizer backend, Bedrock integration, all eight Terraform modules, the CI/CD pipeline with security gates, monitoring/alarms, and CIS security hardening — all within a $50/month budget ceiling. |

### Needs Improvement

* Keep documentation and worklogs up to date **as work happens**, instead of reconstructing them afterwards.
* Deepen security knowledge: several CIS findings (e.g. over-broad pipeline IAM role) were consciously deferred; next time I want to resolve them properly rather than accept them.
* Estimate time more realistically — infrastructure debugging (pipeline, quotas, IAM) consistently took longer than planned.
