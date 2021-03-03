---
layout: post
title: SQS Visibility Timeout
permalink: /:collection/aws/sqs/visibility-timeout
---

- Amount of time that the message is invisible to SQS after a reader picks up the message.
- Provided the job is processed before the visibility timeout expires, the message will then be deleted from the queue.
- If the job is not processed within that time, the message will become visible again and another reader will process it. This could result in the same message being delivered twice.
- Default visibility timeout is 30 seconds, increase if your task takes >30 seconds.
- Maximum is 12 hours.
