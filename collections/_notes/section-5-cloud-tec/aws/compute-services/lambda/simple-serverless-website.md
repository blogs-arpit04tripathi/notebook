---
layout: post
title: Simple Serverless Website
permalink: /:collection/aws/lambda/simple-serverless-website
---

- Using Route53, API Gateway, Lambda, S3

![simple-serverless-website]({{site.cdn}}/aws/serverless/simple-serverless-website.png)

- Create S3 static website hosting bucket (helpmestudy)
- Purchase Route53 DNS helpmestudy.com
- Bucket name and Domain must be same (till .com) for this to work otherwise it will fail.
- Create Lambda Function
    - Author from Scratch
    ![lambda-function-create]({{site.cdn}}/aws/serverless/lambda-function-create.png)
    - Define Function Name, Runtime Language, select Create new role and provide name (MyLambdaRole) and select policy template (Simple microservice permissions)
- Add API Gateway trigger to Lambda
    - Configure Trigger
    ![lambda-function-trigger.png]({{site.cdn}}/aws/serverless/lambda-function-trigger.png)
    - create new method
    ![lambda-function-method.png]({{site.cdn}}/aws/serverless/lambda-function-method.png)
- Actions --> Deploy API
- Route53 --> Hosted Zones(purchased domains) --> Select helpmestudy.com --> Create A Record (ipv4) with Alias as helpmestudy.com
    - here s3 bucketname and dns name should be same else, Alias Target will not be populated with desired entry.
    ![lambda-function-record.png]({{site.cdn}}/aws/serverless/lambda-function-record.png)
