---
layout: post
title: SQS Queue Types
permalink: /:collection/aws/sqs/queue-types
---

- Standard Queue (default)
- FIFO Queues

![]({{site.cdn}}/aws/sqs/sqs-queue-types.png)

# Standard Queue

- Lets you have a nearly-unlimited number of transactions per second.
- Guarantees that a message is delivered ***at least once***. However. occasionally(because of high-distributed architecture that allows high throughput), more than one copy of message might be delivered out of order.
- Standard queues provide ***best-effort ordering*** which ensures that messages are generally delivered in the same order as they are sent.

# FIFO Queues

- FIFO queues complements the standard queue.
- Important Feature
  - ***First In First Out Delivery***
  - ***Exactly once processing***
- Order in which messages are sent and received is strictly preserved and a message is delivered once and remains available until a consumer processes and deletes it; duplicates are not introduced into the queue.
- FIFO queues also support message groups within a single queue.
- FIFO queues are limited to 300 transactions per second (TPS), but have all the capabilities of standard queue.
