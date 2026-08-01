---
title: "Blog 2 - Cognito M2M Authorization"
date: 2026-02-04
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

# AWS Security Blog | How to monitor, optimize, and secure Amazon Cognito machine-to-machine authorization – A few things I learned as an AWS beginner

Hello everyone,

I've been trying to learn more about Cognito, so the other day I read "How to monitor, optimize, and secure Amazon Cognito machine-to-machine authorization" on the AWS Security Blog. The post covers monitoring, cost optimization, and security for the machine-to-machine (M2M) authorization flow in Cognito. After reading it I understood an authorization flow quite different from the one I'm currently using, so I'd like to share. If I misunderstood anything, please correct me.

At first I assumed M2M was just a minor variant of a normal user login. But reading carefully, I learned it's a completely different flow: no user logs in at all. Instead, two systems/services authenticate *with each other* using a client ID and client secret, which is called the OAuth 2.0 client credentials grant.

### How I understand the flow

According to the post, the M2M flow has 6 steps: the app client sends a request with its client ID/secret to Cognito's `/oauth2/token` endpoint, Cognito returns an access token, the app client uses that token to call the resource server, the resource server fetches the JSON Web Key Set (JWKS) from Cognito to verify the token's signature, and only then returns the resource. What I found neat is that this entire process happens server-side, with no login screen anywhere, literally "machines talking to machines."

### The problem the post highlights: cost and monitoring

Cognito charges separately for M2M app clients and for the number of token requests, so without careful monitoring the cost can climb quickly. The post shows real cost charts broken down by day and by account, and on some days more than $24 was spent purely on issuing tokens.

### The optimization and security practices the post suggests

A few points I took away:

- Clients should cache their access token and reuse it until expiry, instead of requesting new tokens constantly
- If a client can't cache tokens itself, you can put API Gateway in front of Cognito's `/oauth2/token` endpoint as a proxy and enable caching there, which reduces the real requests hitting Cognito
- Use AWS Secrets Manager to hold the client ID/secret rather than hardcoding them
- Use AWS WAF to protect the endpoint, even restricting requests to only those coming through the API Gateway proxy, so nothing calls Cognito directly
- Always define scopes at the app-client level following least privilege, avoiding excess permissions

### What I learned from this post

Being new, I had to re-read the sections on API Gateway caching and the WAF allow-list a few times before I could picture the flow, especially the part about using a custom header so only proxied requests are allowed through. But my main takeaway is: authentication isn't just the one "user logs in" pattern I had in mind. M2M is an entirely different problem, with its own distinct cost and security concerns.

My project currently uses the Cognito Hosted UI with a JWT authorizer for users logging in through a web interface, with no M2M flow at all, so this post taught me another Cognito pattern that a future project might well need.

### Closing thoughts

Thank you for reading my little write-up. I'm still learning, so if anything is wrong I'd be grateful for your corrections 🙏

Reference: <https://aws.amazon.com/blogs/security/how-to-monitor-optimize-and-secure-amazon-cognito-machine-to-machine-authorization/>
