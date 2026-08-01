---
title: "Week 9 Worklog"
date: 2026-02-04
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---

### Week 9 Objectives:

Add authentication and a proper API layer in front of the Lambda: a Cognito User Pool with Hosted UI for sign-up/login, an API Gateway REST API exposing the `/summarize` and `/history` routes, a Cognito authorizer protecting both methods, and a usage plan plus CORS to prevent abuse and enable frontend connections.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Configure a Cognito User Pool to manage sign-ups and logins                                                                                   | 06/15/2026 | 06/15/2026      | <https://docs.aws.amazon.com/cognito/latest/developerguide/> | 
| 3   | - Configure OAuth settings and the Hosted UI login page <br> - Debug a `redirect_mismatch` error caused by a mismatch between the callback URL registered in Cognito and the local server's actual address                                              | 06/16/2026 | 06/16/2026      | <https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-user-pools-app-integration.html> |
| 4   | - Create the API Gateway REST API and map the `/summarize` and `/history` routes with Lambda proxy integration | 06/17/2026 | 06/17/2026      | <https://docs.aws.amazon.com/apigateway/latest/developerguide/> |
| 5   | - Create a Cognito Authorizer in API Gateway and attach it to both methods                            | 06/18/2026 | 06/18/2026      | <https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-integrate-with-cognito.html> |
| 6   | - Attach a usage plan with a rate limit and API key <br> - Configure CORS on the methods to enable frontend connections                                                                                     | 06/19/2026 | 06/19/2026      | <https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-request-throttling.html> |


### Week 9 Achievements:

* Configured a Cognito User Pool with email-based sign-up and login.
* Set up OAuth and the Hosted UI, and fixed a `redirect_mismatch` error after login by matching the callback URL registered in Cognito to the local dev server's actual scheme and address.
* Built the API Gateway REST API with `/summarize` and `/history` routes wired to the Lambda via proxy integration.
* Attached a Cognito JWT authorizer to both methods so every request must carry a valid token — the Lambda then identifies the user from the Cognito `sub` claim.
* Protected the API from abuse with a usage plan (rate limit + monthly quota) and an API key, and configured CORS so the browser frontend can call the API.
* Understood the end-to-end auth flow: Hosted UI login → JWT token → API Gateway authorizer validation → user identity available inside the Lambda.
