---
layout: post
title: Netflix Zuul - Server Side Load Balancer
permalink: /:collection/microservices/load-balancing/netflix-zuul
---

**Load Balancing?**  
- In Cloud computing, load balancing improves the distribution of workloads across multiple computing resources.
  - such as computers, a computer cluster, network links, central processing units, or disk drives.
- increase reliability and availability through redundancy.
- Load balancing usually involves dedicated software or hardware, such as a multilayer switch or a Domain Name System server process.
- avoid overload of any single resource.
- optimize resource use
- maximize throughput
- minimize response time

**How to achieve server side load balancing using Spring Cloud?**  
- ***Server side load balancing*** can be achieved using ***Netflix Zuul***.
- Zuul is a JVM based router.
- known as server side load balancer by Netflix.
- We can
  - integrate Zuul with other Netflix projects
    - Hystrix for fault tolerance 
    - Eureka for service discovery
  - use it to manage routing rules, filters, and load balancing across your system.
- It provides a single entry to our system, which allows a browser, mobile app, or other user interface to consume services from multiple hosts without managing cross-origin resource sharing (CORS) and authentication for each one.
