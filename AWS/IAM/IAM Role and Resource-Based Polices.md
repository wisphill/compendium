---
layout: post
description: AWS Identity Center is AWS Solution for single sign on solution. One login for multiple AWS accounts, business cloud apps, SAML2.0-enabled applications, EC2 Window instances.
---

#aws #iam #advanced_policies #assume_role #resource_based

### When using assumeRole (user, application, service), it gives up the original permissions to take permissions that assigned to the role. 

### Event Bridge with Resource based policies.
- When using Bridge to access some service (SQS, SNS, Log, API Gateway), we need to specify resouce based policy to (SQS, SNS, Log, API Gateway)
  Bridge --------> Lambda
- Like Kinesis, ECS task, Run command, we need to assign role to EventBridge (assuming role).