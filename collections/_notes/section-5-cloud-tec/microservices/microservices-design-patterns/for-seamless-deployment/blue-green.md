---
layout: post
title: Blue-Green Deployment
permalink: /:collection/microservices/patterns/blue-green
---

- In a microservice design pattern, there are multiple microservices.
- Whenever updates are to be implemented or newer versions deployed, one has to shut down all the services.
- This leads to a huge downtime thus affecting productivity.
- To avoid this issue, when you design microservice architecture, you should use the blue-green deployment pattern.
- In this pattern, two identical environments run parallelly, known as blue and green.
- At a time only one of them is live and processing all the production traffic.
- For example, blue is live and addressing all the traffic.
- In case of new deployment, one uploads the latest version onto the green environment, switches the router to the same and thus implement the update.