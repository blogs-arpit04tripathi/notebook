---
layout: post
title: Default Partitioner
permalink: /:collection/kafka/partitioner/default
---

- If partition number specified, use it.
- If key specified without partition number, choose partition as per hash of the key.
- If none of the above, assign partition in round-robin fashion.
- return Utils.toPositive(Utils.murmur2(keyBytes)) % numPartitions;
