---
layout: post
title: SQS Introduction
permalink: /:collection/aws/sqs/introduction
---


- Web service that gives access to message queue that can be used to store messages while waiting for server to process them.
- ***SQS is Pull based system, not push-based.***
- Distributed queue system to enable web service applications to quickly and reliably queue messages that one component in application generates to be consumed by other component.
- A queue is temporary repository for messages that are awaiting processing.
- Using SQS, you can decouple the components of an application so they run independently, easing message management between components.
- Any component of a distributed application can store messages in the queue.
- ***Message can contain upto 256KB of text in any format.***
- ***Messages can be kept in the queue from 1 minute to 14 days***
- ***Default retention period is 4 days.***
- Any component can later retrieve the messages programmatically using the Amazon SQS API.
- The queue acts as buffer between the component producing and saving data, and the component receiving the data for processing.
- Queue resolves issues that arise if the producer is faster than the consumer or if the producer or consumer are only intermittently connected to the network.
