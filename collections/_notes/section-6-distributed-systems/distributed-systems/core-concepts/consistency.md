---
layout: post
title: Consistency
permalink: /:collection/distributed-systems/consistency
---

- **Consistency**
  - Assuming you have a storage system which has more than one machine, consistency implies that the data is same across the cluster, so you can read or write to/from any node and get the same data.
  - ***Strongly Consistent***.
- **Eventual consistency**
  - In a cluster, if multiple machines store the same data, an eventual consistent model implies that all machines will have the same data eventually.
  - Its possible that at a given instance, those machines have different versions of the same data ( temporarily inconsistent ) but they will eventually reach a state where they have the same data.