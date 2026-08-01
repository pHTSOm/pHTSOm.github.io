---
title: "Blogs Post"
date: 2026-02-04
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

During the internship, our team researched three articles from official AWS blogs and wrote up what we learned from each. The three posts were chosen to connect with different layers of our graduation project — infrastructure as code, authentication, and deployment strategy:

### [Blog 1 – How CloudFormation express mode accelerates your development cycle](3.1-blog1/)

An AWS DevOps Blog post about CloudFormation's Express mode, which reports a deployment as "done" once resources are configured while full stabilization continues in the background. The key concept I took away: "configured" and "ready to serve" are two different states — something directly relevant to the repeated deploy-test cycles I ran while building our project's CI/CD pipeline with Terraform.

### [Blog 2 – How to monitor, optimize, and secure Amazon Cognito machine-to-machine authorization](3.2-blog2/)

An AWS Security Blog post about the OAuth 2.0 client credentials grant in Cognito — how services authenticate with each other without any user login, why M2M token requests carry their own costs worth monitoring, and how to optimize with token caching, an API Gateway proxy, Secrets Manager, and WAF. A useful contrast with the Hosted UI + JWT authorizer flow our project uses for human users.

### [Blog 3 – How CRED uses Amazon RDS Blue/Green Deployments at scale](3.3-blog3/)

An AWS Database Blog case study on how fintech company CRED automated database upgrades across 120+ RDS/Aurora clusters, cutting 3-hour maintenance windows down to ~2-minute switchovers. The biggest lesson: success comes from preparation — staging parity, gradual traffic shifting, and a rehearsed rollback plan — not from the switchover itself.
