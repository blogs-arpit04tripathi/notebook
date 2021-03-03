---
layout: post
title: Core Concepts
permalink: /:collection/kafka/core-concepts
---

- **Producer**: Application sending messges to Kafka. (Array of bytes)
- **Consumer**: Application reading data from kafka.
- **Broker**: Kafka server
- **Cluster**: A group of computers sharing workload, running 1 instance of broker). Distributed system.
- **Topic**: Unique name for kafka stream.
- **Partitions**: Breaking huge data that is larger than single broker capacity. Each partition sits on a single machine, you cannot break it further.
- **Offset**: Sequence id given to messages as they arrive in a partition. (Immutable). 
    - No global offset for partitions, it’s local to a partition.
- **Consumer groups**:
    -	Group of consumers sharing workload. 
    -	Maximum consumers in group = number of partitions of the topic.
    -	No more than 2 consumers are allowed by kafka to read simultaneously to avoid double reading of records.

![]({{site.cdn}}/kafka/kafka-core-concepts.png)

![]({{site.cdn}}/kafka/concept-consumer-groups.png)
