---
title: "Week 5 Worklog"
date: 2026-02-04
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Objectives:

Focused on mastering global DNS management with Route 53, including hosted zones, DNSSEC, and intelligent traffic routing policies such as weighted and failover routing to ensure performance and resilience. I optimized global user experience through latency, geolocation, and geoproximity routing. Additionally, I transitioned from virtual machines to containerized applications by learning Docker fundamentals and pushing images to ECR, followed by orchestrating containers at scale using ECS and serverless Fargate.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Learn about global entry point for all web traffic                                                                                                   | 05/11/2026 | 05/11/2026      | <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03/>  |
| 3   | - Build a global network that directs user based on performance and health                                              | 05/12/2026 | 05/12/2026      | <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03/> |
| 4   | - Learn about latency and location to optimize user experience | 05/13/2026 | 05/13/2026      | <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03/> |
| 5   | - Learn to create a Docker Image and how to push it to the Elastic Container Retrisgy for secure cloud storage                            | 05/14/2026 | 05/15/2026      | <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03/> |
| 6   | - Orchestrate containers at scale without managing underlying servers                                                                                     | 05/15/2026 | 05/15/2026      | <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03/> |


### Week 5 Achievements:

* Learned about Public/Private zones and why alias record are technically superior to CNAMEs in AWS
* Learned how to use DNSSEC to add digital signatures to domain records, preventing man in the middle DNS attack.
* Understanding the way to updating nameservers at a third party registrar to point to AWS hosted zone so route 534 can routes traffic for a domain registered with a different provider.
* Practiced configuring routing based on percentage and setting up health-check-driven Failover for disaster recovery.
* Learn how to serve users based on the fastest path or their physical country
* Understand that a Dockerfile acts as a source code for the environment, making it repeatable and version-controlled, so Dockerfile is neccessary even though we could just capture an image of a running container.
* Study ECS concepts and cluster mode
* Practiced the Fargate launch type, help me run containers in a serverless fashion without managing EC2 clusters.