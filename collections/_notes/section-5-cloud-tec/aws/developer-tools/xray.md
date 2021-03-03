---
layout: post
title: AWS X-Ray
permalink: /:collection/aws/xray
---

- TOC
{:toc}

<hr><br>

- AWS X-Ray is a service that collects data about requests that your application serves, and provides tools you can use to view, filter, and gain insights into that data to identify issues and opportunities for optimization.
- For any traced request to your application, you can see detailed info not only about the request and response, but also about the calls that your appication makes downstream AWS resources, microservices, databases and HTTP web APIs.

![aws-x-ray.png]({{site.cdn}}/aws/serverless/aws-x-ray.png)

# X-Ray SDK
It provides
- Interceptors to add to your code to trace incoming HTTP requests.
- Client handlers to instrument AWS SDK clients that your application uses to call other AWS Services.
- An HTTP client to use to instrument calls to other internal and external HTTP web services.

![]({{site.cdn}}/aws/serverless/x-ray-overview.png)

- AWS X-Ray SDK sends the data to the X-Ray daemon which buffers segments in a queue and uploads them to X-Ray in batches.
- You need both X-Ray SDK and X-Ray Daemon on your systems.

# X-Ray Integration
X-Ray integrates to following AWS Services
- ELB
- AWS Lambda
- API Gateway
- Elastic Compute Cloud (EC2)
- Elastic BeanStalk

# X-Ray Languages
- Java, Go, Node.js, Python, Ruby, .Net

# X-Ray High Level Configuration Steps
High level requirements
- X-Ray SDK
- X-Ray Daemon

You use the SDK to instrument your application to send the required data eg. data about incoming and outgoing HTTP requests that are being made to your Java application.

On-Premise or EC2 Instances
- Install X-Ray Daemon to your EC2 instance or on-premise server.
Elastic Beanstalk
- Install X-Ray Daemon on the EC2 instances inside your EBS environment.
Elastic Container Service
- Install X-Ray daemon in its own docker container on your ECS cluster alongside your app.

# Annotations and Indexing
**Annotations** 
- When instrumenting your application, you can record additional information about requests by using annotations.
- Annotaions are simply Key-Value Pairs that are indexed for use with filter expressions, so that you can search for traces that contain specific data and group related traces together in the console - eg. game_name=TicTacToe, game_id=2645445842

