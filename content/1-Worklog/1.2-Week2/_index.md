---
title: "Week 2 Worklog"
date: 2026-02-04
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives:

* Learn how to design systems that automatically recover from failure and scale with demand.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 5   | - Studied the role of Application Load Balancers (ALB) in distributing incoming application traffic accross multiple targets (EC2 instances) in different Availability Zones                                                                                                   | 04/09/2026 | 04/09/2026      | <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03>|
| 6   | - What is No-Ops, study about event-driven                                              | 04/10/2026 | 04/10/2026      | <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03> |
| 2   | - Learn about the differences between relation and non-relational data storage, and know which type storage to use in different scenerios| 04/13/2026 | 04/13/2026      | <https://master.d31mm2rc5713dr.amplifyapp.com/#/course/week-4:-storage-services-on-aws> <br> <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03>|
| 3   | - Learn how to use CloudFront and learn how to read CloudWatch metrics                            | 04/07/2026 | 04/07/2026      | <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03> |
| 4   | - Learn to store sensitive information with AWS Secrets Manager                                                                                      | 04/08/2026 | 04/08/2026      | <https://master.d31mm2rc5713dr.amplifyapp.com/#/course/week-5:-security-services-on-aws/> <br> <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03>  |


### Week 2 Achievements:

* Studied the role of Application Load Balancers (ALB) in distributing incoming application traffic across multiple targets (EC2 instances) in different Availability Zones.

* Know how to use Auto Scaling Group to automatically add or remove EC2 instances based on health checks or CPU utilization metrics.

* Explore event driven computing with AWS Lambda, where code runs in response to triggers without the need to provision or manage underlying servers.

* Get to know why Amazon RDS provide High Availability with Multi-AZ deployments and how Read Replicas help with scaling read-heavy workloads

* Studied the fundamentals of Key Value databases, learn about partition keys, sort keys, and why Nosql is preferred for high speed, infinite scaling compared to traditional SQL.

* Discover how Amazon Cloudfront can help cache static and dynamic content at edge locations to reduce latency for users located far from the origin server.

* Learn using Amazon Cloudwatch to minitoring operational health by setting up Alarms for CPU usage and creating Dashboards to visualize system performance.

* Studied Envelope Encryption and how to manage cryptographic keys to encrypt data at rest in S3 and RDS.

* Learned how to securely store and rotate sensitive information like database credentials and API keys using AWS Secrets Manager


