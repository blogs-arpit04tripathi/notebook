---
layout: post
title: Branch Pattern
permalink: /:collection/microservices/patterns/branch
---

- Extend Aggregator design patterns - here request not passed sequentially.
- You can simultaneously process the request and response from 2 mutually exclusive chains of microservices.
- Offers flexibility to summon separate multiple chains or even a single chain in accordance to your business needs.
- used to retrive data from multiple sources.
- In case of an eCommerce website or web application we may need to retrieve data from multiple sources belonging to different microservices. This is where Branch Microservice Design Pattern plays an effective role.
