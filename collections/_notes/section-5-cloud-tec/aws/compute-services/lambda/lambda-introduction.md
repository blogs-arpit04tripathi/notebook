---
layout: post
title: Lambda Introduction
permalink: /:collection/aws/lambda/introduction
---

- TOC
{:toc}

<hr><br>

# What is Lambda?
- ***AWS Lambda*** is a compute service where you can upload code and create lambda functions. AWS lambda takes care of provisioning and managing the servers that you use to run the code. You don't have to worry about the OS, patching, scaling etc.
- You can use Lamda in following ways
    - As an event driven compute service where AWS Lambda runs your code in response to events. These events could be changes in data in ana Amazon S3 bucket or an Amazon DynamoDB table.
    - As a compute service to run your code in response to HTTP requests using amazon API Gateway or API calls made using AWS SDKs, This is what is used at Cloud Guru.

* Cloud Guru hosts everything on AWS with videos stored in S3 with CloudFront as CDN provider
  - These videos are stored in a Data Centres
  - Data Centres have Hardware, things like Sands, Servers, Switches, Routers, Firewalls, load balancers etc.
  - These devices use Assembly code/Protocols
  - Developers learn High Level Languages
- To use these languages we have Operating Systems
- Interaction happens either via Application Layer(Chrome, explorer etc.) or via AWS APIs when using console
  - Final Layer of abstraction is AWS Lambda, any api calls to api gateway  triggers lambda functions in background.
* So, Lamda is the latest abstraction layer which means you only have to worry about the codem other things are taken care of by Lambda.

# How is Lamda Priced ?
- Number of Requests
    - First 1 million req are free, 0.2$ per million requests per month thereafter.
- Duration
    - Duration is calculated from time when your code begins executing until it returns or otherwise terminates, rounded up to nearest 100ms. The price depends on the amount of memory allocated to your function.
    - You are Charged $0.00001667 for every GB-second use.

# Why is Lambda Cool?
- No Servers - No System, database, network administrators
- Continuous Scaling - Lamda scales out(not up) automatically.
- Cost effective
- Lambda functions are independent, 1 event = 1 function
- When talking to alexa, you are talking to Lambda.
- Lamda funtions can trigger other lambda functions, 1 event can = x functions if functions triggers other functions.
- Architectures can get extremely complicated, AWS X-ray allows you to debug what is happening.
- Lambda can do things globally, you can use it to backup S3 buckets to other S3 buckets etc.
- You should know your lambda triggers.

# Lambda Concurrent Execution Limit
- Safety feature to limit the number of concurrent executions across all functions in a given region per account.
- Default 1000 per region, 429-TooManyRequestsException for Request throughput limit exceeded.
- You can request an increase in this limit by submitting a request to AWS support center.
- **Reserved Concurrency** guarantees that a set number of executions which will always be available for your critical function, however this also acts as limit.
