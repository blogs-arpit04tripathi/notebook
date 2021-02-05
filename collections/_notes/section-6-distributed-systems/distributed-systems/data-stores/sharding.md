---
layout: post
title: Sharding
permalink: /:collection/distributed-systems/sharding
---

- With most huge systems, data does not fit on a single machine. In such cases, sharding refers to splitting the very large database into smaller, faster and more manageable parts called data shards.
- Logical partitioning of server.
- example - column countryName used for sharding will make unequal size of partition after sharding.
- partition here can be of big size hence use pf kafka is popular.
- RDB can solve big data problem if join can be removed but normalization will go away hence not feasible.

**Why can't we use Sharding for big data problems**
- Sharding is Logical partitioning to server to make small
  - example - column country used for sharding, this makes unequal size of partitions after sharding.
  - partition here can be of big size hence use of kafka is popular.
- Relational DB can solve big data problem if join can be removed but normalization will be compromised hence not feasible option.
  - Here, we shard data based on country then, high population density countries will put more load on server for the same operation being performed on other partition.
  - SQL Query - Chain of SQL operations (bottom-up approach), uses DAG(Directed Acyclic Graph)
- Kafka - provides on demand scale up/ scale down.
- index scan (kafka) => table scan (RDBMS)