---
layout: post
title: Elasticache Introduction
permalink: /:collection/aws/elasticache/introduction
---

* Elasticache is a web service to deploy, operate and scale an in-memory cache in cloud.
* The service improves performance of web applications by allowing you to retrieve information from fast, managed, in-memory caches, instead of relying on slower disk-based DB.
* Sits between you application and DB.
* Takes load off your DB.
* Good if your DB is particularly read-heavy and data is not changing frequently.
* Used to significantly improve latency and throughput for many 
    - read-heavy application-workloads(such as social networking, gaming, media sharing and Q&A portals) or
    - compute-intensive workloads(such as a recommnedation engine)
* Caching improves appilcation performance by storing critical pieces of data in memory for low latency access.
* Cached info may include
    - results of IO intensive DB queries.
    - results of computationally intensive calculations.
