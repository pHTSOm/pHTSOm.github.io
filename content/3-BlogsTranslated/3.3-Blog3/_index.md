---
title: "Blog 3 - RDS Blue/Green Deployments"
date: 2026-02-04
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# AWS Blog | How CRED uses Amazon RDS Blue/Green Deployments at scale – A few things I learned as an AWS beginner

Hello everyone,

I've been trying to learn about blue/green deployments for databases, so the other day I read "How CRED uses Amazon RDS Blue/Green Deployments at scale" on the AWS Blog. The post is about CRED — a fintech platform in India — and how they automated database upgrades across more than 120 RDS/Aurora clusters. I understood quite a few new things after reading it, so I'd like to share — if I misunderstood anything, please correct me.

At first I assumed blue/green deployment was simply having 2 copies of a database and switching between them. But reading carefully, I realized the hardest part isn't the switchover itself — it's all the preparation that comes before it.

### How I understand the problem

According to the post, whenever CRED previously wanted to upgrade a database version or change instances, they had to plan a maintenance window of about 3 hours, with heavy coordination effort and downtime risk. With more than 120 clusters, that manual approach no longer worked. I found this number easy to relate to: just imagine how exhausting doing that by hand would be for even a few dozen databases.

Blue/green deployment solves this by creating a copy (green) running alongside the main database (blue), kept in sync through replication. All changes are made on green first, and only then comes the "switchover" — moving traffic from blue to green — which according to the post takes only about 2 minutes on average.

### What I found most interesting: the preparation

This part genuinely surprised me: CRED says that across 200 migrations, 90% of the success came from thorough preparation, not from the switchover itself. Some things they do before switching over:

- Test thoroughly on a staging environment identical to production — if staging tests fail, production doesn't happen (no exceptions)
- Share the green endpoint with application teams early so they can test in advance, and require sign-off before any switchover
- For major version upgrades, replay production queries against both versions and compare the results
- Shift read traffic to green gradually — 10% → 50% → 100% over several days — before switching completely

I think this "gradual shift" approach is quite smart — instead of blindly trusting the green copy, they make it prove itself with real traffic first.

### What I learned from this post

Being new, several terms in the post (CDC pipeline, checkpoint, reverse replication) took me a few re-reads to roughly understand. But my main takeaway is: rollback matters just as much as switchover. The post describes an incident where a problem was discovered 20 minutes after a switchover — and because they had already rehearsed the rollback procedure, they returned to the old version in just 2.5 minutes with no data loss. Without preparing rollback from the start, that situation would have been far more stressful.

My project currently uses DynamoDB, so I haven't touched RDS/Aurora yet, but this post helped me understand the blue/green concept at the database layer — maybe I'll get to apply it someday.

### Closing thoughts

In my opinion, "How CRED uses Amazon RDS Blue/Green Deployments at scale" is quite a detailed post — not just theory, but a real case study with concrete numbers. If you're just starting to learn about blue/green deployments like me, I think it's worth reading, though take it slowly since there's a lot of terminology.

Thank you for reading my little write-up — I'm still learning, so if anything is wrong I'd be grateful for your corrections 🙏

Reference: <https://aws.amazon.com/blogs/database/how-cred-uses-amazon-rds-blue-green-deployments-at-scale/>
