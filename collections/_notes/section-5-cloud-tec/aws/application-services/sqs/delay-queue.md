---
layout: post
title: SQS Delay Queue
permalink: /:collection/aws/sqs/delay-queue
---

- Postpone delivery of new message to a queue for number of seconds.
- Message sent to a delay queue remains invisible to customers for the duration of the delay period
- Default delay is 0 seconds, max is 900 seconds (15 Minutes).
- For standard queues, changing the setting doesn't affect the delay of messages already in the queue, only new messages.
- For FIFO queues, this affects the delay of messages already in the queue.

# When to use Delay Queues
- Large distributed applications which may need to introduce a delay in processing.
- You need to apply a delay to an entire queue of messages.
- eg. adding a delay of few seconds to allow for updates to your sales and stock control databases before sending a notification to a customer confirming an online transaction.
