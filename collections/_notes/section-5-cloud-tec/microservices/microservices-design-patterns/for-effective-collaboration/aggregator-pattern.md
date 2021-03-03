---
layout: post
title: Aggregator Pattern
permalink: /:collection/microservices/patterns/aggregator
---

- Multiple microservices, fetching the output and combining it for the end-user is necessary.
- For a user to combine the data, will require immense internal knowledge of the system.
- The solution can be forwarded to the end-user through two major components.
  - The first one is a composite microservice followed by API gateways.
  - Either of them will aggregate the data and forward it to the user.
  - But, in case business capabilities are used in decomposing the system, composite microservice should be preferred.
- Collects related items of data and displays them.
- Based on DRY Principle.

![]({{site.cdn}}/webservices/microservices/aggregator-pattern.png)