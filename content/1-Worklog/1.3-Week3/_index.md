---
title: "Week 3 Worklog"
date: 2026-02-04
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:

Focused on advancing from basic server setup to professional automation and observability. Worked on securely managing EC2 fleets with SSM and architecting the transition from a monolithic server to a decoupled application-database tier.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 5   | - Master automated instance configuration to ensure consistency with "infrastructure as code."                                                                                                   | 04/16/2026 | 04/16/2026      | <https://docs.aws.amazon.com/AWSCloudFormation/latest/TemplateReference/cfn-init.html>  <br>  <https://docs.aws.amazon.com/AWSCloudFormation/latest/TemplateReference/aws-resource-init.html>
| 6   | - Implement "Least Privilege" security and centralize application secrets.                                              | 04/17/2026 | 04/17/2025      | <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03> <br>  <https://docs.aws.amazon.com/systems-manager/latest/userguide/sysman-paramstore-versions.html> |
| 2   | Implement system-level logging and performance tracking. | 04/20/2026 | 04/20/2026      | <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03/> |
| 3   | - Optimize the physical and logical placement of servers for performance and reliability                            | 04/21/2026 | 04/21/2026      | <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03> <br> <https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html>|
| 4   | - Understand the shift from running databases on servers to using AWS RDS                                                                                     | 04/22/2026 | 04/22/2026      | <https://aws.amazon.com/compare/the-difference-between-acid-and-base-database/> <br>  <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03/> |


### Week 3 Achievements:

* I know how the cfn-signal command works to tell the stack that the EC2 instance is fully initialized, I realized cfn-init allows for easier state managemennt and updates without needing to replace the entire instance
* Learned that the advanced parameters allow for larger values and higher throughput but incur a cost
* Learned to use SSM Parameter Store to store sensitive data.
* Study about Cluster, Spread and Partition placement groups. I also learn about enable ENA for consistent networkk throughput.
* I understand that Partition placement groups provide the best balance of isolation and performance.
* Understand data consitency by reading article about ACID vs BASE, studied the architectural process of splitting a WordPress monolith by moving the database from an EC2 instance into a dedicated RDS instance
