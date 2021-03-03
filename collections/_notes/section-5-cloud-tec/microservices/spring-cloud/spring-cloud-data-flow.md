---
layout: post
title: Spring Cloud Data Flow
permalink: /:collection/microservices/spring-cloud-data-flow
---

**What is Spring Cloud Data Flow? Need for it?**  
Spring Cloud Data Flow is a toolkit to build real-time data integration and data processing pipelines by establishing message flows between Spring Boot applications that could be deployed on top of different runtimes.

Long lived applications require Stream Applications while Short lived applications require Task Applications.

In this example we make use of Stream Applications. Previously we had already developed Spring Cloud Stream applications to understand the concept of [Spring Cloud Stream Source](https://www.javainuse.com/spring/cloud-stream-rabbitmq-1) and [Spring Cloud Sink](https://www.javainuse.com/spring/cloud-stream-rabbitmq-2) and their benefit. 

![]({{site.cdn}}/webservices/microservices/spring-cloud-data-flow.png)

Pipelines consist of Spring Boot apps, built using the Spring Cloud Stream or Spring Cloud Task microservice frameworks. SCDF can be accessed using the REST API exposed by it or the web UI console.

We can make use of metrics, health checks, and the remote management of each microservice application Also we can scale stream and batch pipelines without interrupting data flows. With SCDF we build data pipelines for use cases like data ingestion, real-time analytics, and data import and export. SCDF is composed of the following Spring Projects.

![]({{site.cdn}}/webservices/microservices/spring-cloud-data-flow-modules.png)

# Distributed Transactions

**How will you define the Distributed Transactions?**  
This is the situation where a single event results in the mutation of two or more sources of separate data that cannot be committed automatically.
