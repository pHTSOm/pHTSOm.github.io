---
title: "Week 4 Worklog"
date: 2026-02-04
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---



### Week 4 Objectives:

Focused on mastering the deployment and migration of managed relational databases using RDS, ensuring high availability and disaster recovery with Multi-AZ setups and backups, scaling read performance with Read Replicas while managing replication lag, exploring Amazon Aurora’s cloud-native architecture and serverless features, and managing global scaling alongside efficient connection pooling using Aurora Global Database and RDS Proxy.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Master the deployment and migration of managed relational databases                                                                                                   | 05/04/2026 | 05/04/2026      |  <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03> <br> <https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_DMS_migration.html> |
| 3   | - Ensure data persistence and 24/7 availability for critical applications                                               | 05/05/2026 | 05/05/2026      | <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03> <br> <https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html> |
| 4   | - Learn to scale database performance for read-heavy workkloads | 05/06/2026 | 05/06/2026      | <https://docs.aws.amazon.com/whitepapers/latest/best-practices-wordpress/reference-architecture.html>  <br>  <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03> |
| 5   | - Explore the Cloud Native high performance database tier                            | 05/07/2026 | 05/07/2026      | <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03> |
| 6   | - Manage global data reach and high-volume connection pooling                                                                                     | 05/08/2026 | 05/08/2026      | <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03/> |


### Week 4 Achievements:

* Studied the different RDS instance classes and storage types. Practiced migrating a EC2-hosted database into RDS using DMS
* Learned about synchronous replication and automatic failover. Practiced managing automated backups and manual snapshots for long term recovery
* Understand that snapshots are immutable backups, ensuring user never accidentally overwrite existing data during a recovery that's why snapshot restore creates a brand new RDS instance rather than updating the old one
* Learned how asynchronous replication allows for up to 15 read replicas, offloading ddheavy query traffic from the primary writer instance.
* Learned how to handle stale data when a read replica hasn't finished syncing from the primary by ensures sensitive write then read operations always hit the primary instance.
* Explored Aurora serverless for applications with unpredictable traffic patterns
* Study global databases for sub-second global latency and RDS proxy for managing thousands of concurrent application connections efficiently.