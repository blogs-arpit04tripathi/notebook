---
layout: post
title: Kinesis Consumers/Kinesis Client Library
permalink: /:collection/aws/kinesis/consumer
---

- Kinesis client library runs on the consumer instances.
- Tracks the number of shards in your stream.
- Discovers new shards when you reshard.
- KCL ensures that each consumer has a record processor.
- Manages the nuumber of record processors relative to the number of shards and consumers.
- If you have only one consumer, KCL will create all the record processors on a single consumer.
  - If you have 2 consumers it will load balance and create half the processors on each instance.
- With KCL, generally you should ensure that the number of instances does not exceed the number of shards (except for failure or standby purposes).
- You never need multiple instances of consumer to process load of 1 shard, however 1 consumer can process multiple shards.
- It is fine if number of shards exceeds the number of instances.
- Don't think that just because you reshard, you need to add more instances.
- Instead CPU Utilizatin is what should drive the quantity of consumer instances you have, not the number of shards in your kinesis streams.
- Use an autoscaling group, and base scaling decisions on CPU load of your consumers.
