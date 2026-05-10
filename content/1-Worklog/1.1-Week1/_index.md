---
title: "Week 1 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Week 1 Objectives:

* Study networking fundamentals (OSI model, IP addressing/CIDR, NAT variations).
* Understand AWS physical and logical infrastructure.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 5   | - Understand the theoretical framework of data transmission and addressing                                                                                                   | 04/02/2026 | 04/02/2026      | <https://master.d31mm2rc5713dr.amplifyapp.com/#/course/week-1:-introduction-to-aws> <br> <https://learn.cantrill.io/p/tech-fundamentals>|
| 6   | - Learn how traffic routing works and what the AWS physical footing is                                              | 04/03/2026 | 04/03/2026      | <https://master.d31mm2rc5713dr.amplifyapp.com/#/course/week-1:-introduction-to-aws> <br> <https://learn.cantrill.io/p/tech-fundamentals> |
| 2   | - Start implement some foundational building blocks of a cloud environment| 04/06/2026 | 04/06/2026      | https://master.d31mm2rc5713dr.amplifyapp.com/#/course/week-2:-networking-on-aws> <br> <https://master.d31mm2rc5713dr.amplifyapp.com/#/course/week-3:-compute-vm-service-on-aws> <br>  <https://master.d31mm2rc5713dr.amplifyapp.com/#/course/week-4:-storage-services-on-aws> |
| 3   | - Utilize centralized identity and access control to protect the cloud environment                            | 04/07/2026 | 04/07/2026      | <https://master.d31mm2rc5713dr.amplifyapp.com/#/course/week-5:-security-services-on-aws> <br> <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03> |
| 4   | - Learn how to provision AWS services automatically                                                                                     | 04/08/2026 | 04/08/2026      | <https://master.d31mm2rc5713dr.amplifyapp.com/#/course/week-5:-security-services-on-aws/> <br> <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03>  |


### Week 1 Achievements:

* Review all 7 layer of OSI model:
  * Physical Layer
  * Data Link Layer
  * Network Layer
  * Transport Layer
  * Session Layer
  * Presentation Layer
  * Application Layer

* Studied the IP address space and know how to calculating subnets with CIDR notation to define network boundaries and broadcast domains

* Learn about Network Address Translation (NAT) by analyzed how private IP addresses communicate with the public internet through NAT 

* Learn the difference between: 
  * Static NAT  
  * Dynamic NAT 
  * PAT (Port Address Translation)

* Learn the Fundamentals of:  
  * Virtual Private Cloud   
  * Elastic Compute Cloud   
  * Simple Storage Service

* Learn the creation of with IAM:  
  * Users   
  * Groups   
  * Roles

* Practiced writing JSON policies to enforece the "Principle of Least Privilege" for resource access

* Explored the concept of an AWS Account as the primary security and billing boundary, and how it isolates resources from other environments

* Categorized AWS services to understand which require VPC placement and which are globally accessible via public endpoints

* Get to know the concept of Infrastructure as Code with CloudFormation

*  Learned how to link multiple AWS accounts into a single Organization, utilizing Organizational Units for logical grouping

* Find out about Service Control Policies and try to analyzed how to apply administrative guardrails accross an entire organization