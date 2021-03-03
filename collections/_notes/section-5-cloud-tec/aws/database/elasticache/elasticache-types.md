---
layout: post
title: Types of Elasticache
permalink: /:collection/aws/elasticache/types
---

* Elasticache supports two open-source in-memory caching engines
    - **Memcached**
        - Widely adopted memory object caching system
        - Multi-threaded
        - No Multi-AZ capability.
    - **Redis**
        - Open source in-memory key-value store
        - Supports more complex data structures: sorted sets and lists
        - Supports Master/Slave replication and Multi-AZ for cross AZ redundancy.

# Redis
* Popular open-source in-memory key-value store that supports data structures such as sorted sets and lists.
* Elasticache supports master-slave replication and multi-AZ which can be used to achieve cross AZ redundancy.
* Because of replication and persistence feature, Elasticache manages Redis more as a Relational DB.
* Redis Elasticache clustures are managed as stateful entities that include failover, similar to how RDS manages DB failover.

**Use Cases - Redis**
* Looking for more advanced data types, such as lists, hashes and sets.
* Sorting and ranking datasets in memory help you, such as with leaderboard.
* Persistence of your key stores is important.
* Want to run in multiple AWS Availability Zones with failover.

# Memcached
* Designed as pure caching solution with no persistence, Elasticache manages Memcached nodes as a pool that can grow or shrink similar to EC2 auto scaling group.
* Individual nodes are expendable, and elasticache provides additional capabilities such as automatic node replacement and Auto Discovery.

**Use Cases - Memcached**
* Is object caching is your primary goal, for example to offload your DB?
* Interested in simple caching model.
* Planning on running large cache nodes, and require multithreaded performance with utilization of multiple cores.
* Want an ability to scale your cache horizontallly as you grow.
