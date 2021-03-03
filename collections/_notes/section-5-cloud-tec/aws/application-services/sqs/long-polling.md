---
layout: post
title: SQS Long Polling
permalink: /:collection/aws/sqs/long-polling
---

- SQS uses Long Polling for retrieving messages from queue.
- While Regular Short Polling returns immediately(even if the queue is empty), Long Polling doesn't return a response until a message arrives in the message queue, or the Long Polling times out.
- Maximum long poll time out is 20 seconds.
- As such, Long Polling can save you money.