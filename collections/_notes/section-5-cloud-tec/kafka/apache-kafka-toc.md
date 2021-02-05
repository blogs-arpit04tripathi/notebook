---
layout: post
title: Apache Kafka
permalink: /:collection/kafka/
---

- [Kafka Introduction](introduction)
  - [Kafka vs Queue](kafka-vs-queue)
  - [Integration Problem](integration-problem)
- [Core APIs](core-apis)
- [Core Concepts](core-concepts)
- [Kafka CLI](cli)
- [Kafka Broker Configuration](broker-config)
  - [Fault Tolerance](fault-tolerance)
- [Producer API](producer/api)
  - Partitioner
    - [Default Partitioner](partitioner/default)
    - [Custom Partitioner](partitioner/custom)
  - [Custom Serializers](serializer/custom)
  - [Producer Config](producer/config)
  - [Asynchronous Call (Caution)](producer/async-caution)
- [Consumer API](consumer/api)
  - [Consumer Config](consumer/config)
  - [Offsets](consumer/offsets)
    - [Commit Current Offset](consumer/commit-current-offset)
    - [Commit Specific Offset](consumer/commit-specific-offset)
  - [RebalanceListener](consumer/rebalance-listner)
- [Schema Evolution (Avro Schemas)](schema-evolution)
- [To Do](todo)

