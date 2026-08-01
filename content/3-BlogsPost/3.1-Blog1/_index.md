---
title: "Blog 1 - CloudFormation Express Mode"
date: 2026-02-04
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# AWS DevOps Blog | CloudFormation Express Mode – A few things I learned as an AWS beginner

Hello everyone,

I've only been learning AWS for a little while and I'm still getting familiar with CloudFormation, so I often read the AWS Blog to understand more. The other day I read the post "How CloudFormation express mode accelerates your development cycle" and found it quite approachable (though I did have to re-read it a few times at first), so I'd like to share what I understood. If I got anything wrong, please correct me.

At first I assumed this was simply an option to deploy faster. But reading carefully, I realized it isn't just about speed. It changes what CloudFormation actually means when it tells you a deployment is "done."

### How I understand the problem

According to the post, when you normally deploy a resource, CloudFormation doesn't report completion the moment the resource is created. It waits until the resource is truly ready to operate (this is called "stabilization"). For example, a CloudFront distribution takes 5 to 10 minutes to propagate to all the edge locations around the world. That makes sense for a production deployment, but if you're just testing over and over while learning or coding, it feels slow. You don't need real traffic yet; you just want to know whether your configuration is correct.

### So what does Express mode help with?

My rough understanding after reading: Express mode lets CloudFormation report "done" as soon as a resource is *configured*, while full stabilization continues in the background. What I liked is that it still tells you which resources are configured and which are still stabilizing in the background, so the information isn't hidden. And the dependency ordering between resources (which one must be created before which) is preserved exactly as normal, nothing gets shuffled.

One detail I found quite interesting is that it disables automatic rollback by default. At first this surprised me because I'd always assumed automatic rollback was a good thing, but reading further I understood: when you're iterating quickly, an automatic rollback to the previous state on failure destroys the very context you need to debug the error. Turning it off so you can fix things in place makes more sense for development.

### What I took away

Since I'm still new, I read this post mostly to learn the concepts, and I wouldn't claim to understand it 100% deeply. But the best thing I learned is a new distinction: "configured" and "ready to serve" are two different things, and they don't always arrive together. Until now I had simply assumed that once a deployment finishes, everything is immediately usable.

While working on the backend and CI/CD for my graduation project, I sometimes deploy repeatedly just to grab an ID or an endpoint for the next step, so this post described exactly the kind of situation I run into, even though I mainly use Terraform and am not yet fluent in CloudFormation.

### Closing thoughts

In my opinion, "How CloudFormation express mode accelerates your development cycle" is an accessible read for beginners like me, and it helps you understand how CloudFormation works behind the scenes. If you're also new to AWS, I think it's worth a read. You'll come away with a clearer picture of the "stabilize" concept that I, for one, had never paid attention to before.

Thank you for reading my little write-up. I'm still learning, so if anything is wrong I'd be grateful for your corrections 

Reference: <https://aws.amazon.com/blogs/devops/how-cloudformation-express-mode-accelerates-your-development-cycle/>
