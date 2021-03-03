---
layout: post
title: Asynchronous Call (Caution)
permalink: /:collection/kafka/producer/async-caution
---

- It may happen that due to retries, the sequence of messages sent to kafka are mixed up.
- For the cases where sequence is critical, either use
  - Synchronous send
  - `max.in.flight.requests.per.connection=1`

![]({{site.cdn}}/kafka/producer-async-batch.png)
