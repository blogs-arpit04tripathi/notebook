---
layout: post
title: Lambda and VPC
permalink: /:collection/aws/lambda/lambda-and-vpc
---

![]({{site.cdn}}/aws/serverless/lambda-and-vpc.png)

- Some usecases require lambda to access resources which are inside a private VPC.
- eg. read or write a RDS daabase, or shut down an EC2 instance in response to security alert.

# Enabling Lambda to Access VPC Resources
- To enable this, you need to allow the finction to connect to private subnet.
- Lambda needs the following VPC Configuration information so that it can connect to VPC
  - Private subnet id
  - Security group id (eith required access)
  - lambda uses this information to setup ENI(Elastic Network Interfaces) using an available ip address from your private subnet.
- Add `vpc-config` parameter to your lambda

```
aws lambda update-function-configuration --function-name my-function --vpc-config SubnetIds=subnet-1122aabb,SecurityGroupIds=sg-51530134
```
