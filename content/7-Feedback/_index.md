---
title: "Sharing and Feedback"
date: 2026-02-04
weight: 7
chapter: false
pre: " <b> 7. </b> "
---

> Personal reflections on my experience with the First Cloud Journey program, shared in the hope that they help the FCJ team keep improving the program.

### 1. Impressions of the Program

What sets FCJ apart from a normal course is the structure: five weeks of guided self-study on AWS fundamentals, followed by seven weeks applying that knowledge to a real project on a real AWS account — with real consequences. Reading about IAM least privilege is one thing; having tfsec block your own pipeline until you scope a policy down is another. The self-study materials (curated courses and workshops) were well-chosen, and the freedom to pick our own graduation project meant we were genuinely invested in the result.

The program also quietly teaches things no tutorial covers: working within a monthly budget ceiling, opening a real AWS Support case when a service quota blocks you, coordinating shared infrastructure with a teammate through branch protection and pull requests, and cleaning up an account before handover. These "operational" lessons ended up being some of the most valuable ones.

### 2. Satisfaction Level

**Very satisfied — 9/10.** By the end of the program I had gone from having only classroom knowledge to independently designing, building, securing, and operating a complete serverless platform with CI/CD and monitoring — something I can demonstrate live and discuss in depth in job interviews. The one point deducted reflects the areas mentioned below rather than any fundamental problem.

### 3. Areas for Improvement

* **An architecture review checkpoint before building.** Our design was only reviewed after implementation had started. A short mentor review of the proposed architecture at the end of the design week would catch expensive or impractical decisions earlier.
* **A heads-up about new-account limitations.** We lost real testing time to a zero on-demand quota for Bedrock models on a fresh AWS account — something the program could warn teams about in advance (with guidance to file quota requests in week one).
* **A midpoint progress review.** A brief formal check-in around week 9 would help teams catch scope and timeline drift while there is still time to adjust.
* **More peer interaction between teams.** Most of our contact was within our own two-person team; a periodic session where teams demo progress to each other would spread lessons learned (and surface common problems like quota issues faster).

### 4. Would I Recommend the Program to Friends?

**Yes, without hesitation** — with one caveat. I would recommend it to any friend who wants to work in cloud or backend engineering, because it is the closest thing to real professional experience a student can get: a real cloud account, a real budget, real security scanners failing your build, and a deliverable you fully own from architecture to operations. A completed FCJ project is a portfolio piece, not a certificate.

The caveat: it rewards self-direction. The program provides the roadmap and support, but nobody stands over you daily — a friend expecting a lecture-style experience with assignments handed to them would struggle. For anyone willing to drive their own project, though, I can't think of a better preparation.
