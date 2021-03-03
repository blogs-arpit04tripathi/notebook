---
layout: post
title: Log Aggregation
permalink: /:collection/microservices/patterns/log-aggregation
---

Monitoring the performance
- helps calculate the efficiency 
- understand drawbacks slowing the system down
- ensuring robustness

**Who creates logs**
- application is consisting a number of microservices.
- run independently and simultaneously
- runs multiple instances
- Every service generates an entry in the logs regarding its execution.

**How can you keep a track for numerous service related logs?**
- This is where log aggregation steps in.
- Best practice to prevent from chaos, have a master logging service.
- This master logging service should be responsible for aggregating the logs from all the microservice instances.
- This centralized log should be searchable, making it easier to monitor.

