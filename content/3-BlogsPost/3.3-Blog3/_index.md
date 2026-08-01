---
title: "Blog 3 - RDS Blue/Green Deployments"
date: 2026-02-04
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# AWS Blog | How CRED uses Amazon RDS Blue/Green Deployments at scale – A few things I learned as an AWS beginner

Hello everyone,

I've been learning about database blue/green deployments lately, so the other day I read the article "How CRED uses Amazon RDS Blue/Green Deployments at scale" on the AWS Blog. It's about CRED, a fintech platform in India, and how they automate database upgrades across more than 120 RDS/Aurora clusters. After reading it, a lot of the details stuck with me, so I'd like to share what I understood. If I got anything wrong, please let me know.

At first I thought blue/green deployment just meant having two database copies and switching back and forth. But reading more carefully, I realized the hardest part isn't the switchover itself, it's the preparation beforehand.

### How I understand the problem

According to the article, in the past, every time CRED wanted to upgrade a database version or change instance types, they had to plan a maintenance window of about 3 hours, with a lot of coordination and the risk of downtime. With more than 120 clusters, doing this manually was no longer sustainable. That number is easy to picture: just imagine doing it by hand for dozens of databases and how exhausting that would be.

Blue/green deployment solves this by creating a copy, called green, that runs in parallel with the main database (blue) and stays in sync through replication. All changes are applied to green first, and only then comes the "switchover" that moves traffic from blue to green, which the article says takes about 2 minutes on average.

### What I found most interesting: the preparation

When I got to this part I was quite surprised: CRED says that across more than 200 migrations, 90% of their success comes down to careful preparation rather than the switchover itself. A few things they do before switching over:

- Test thoroughly on a staging environment that is identical to production; if the staging tests fail, they don't run it on production (no exceptions)
- Share the green endpoints with the application teams early so they can test in advance, and require sign-off before the switchover
- For major version upgrades, replay production queries against both copies to compare the results
- Gradually shift read traffic to green in stages (10% → 50% → 100%) over a few days before fully cutting over

### What I learned from this post

The article describes a case where a problem was found 20 minutes after the switchover, and because they had already tested the rollback process, they were able to go back to the old version in just 2.5 minutes with no data loss. If they hadn't prepared for rollback from the start, that situation would have been a lot more stressful.

My current project uses DynamoDB, so I haven't touched RDS/Aurora yet, but reading this helped me understand the blue/green concept at the database layer, which I might get a chance to apply someday.

### Closing thoughts

Thank you for reading my little write-up. I'm still learning, so if anything is wrong I'd be grateful for your corrections

Reference: <https://aws.amazon.com/blogs/database/how-cred-uses-amazon-rds-blue-green-deployments-at-scale/>
