---
layout: post
title: NoSQL Data Stores
permalink: /:collection/distributed-systems/nosql
---

- MongoDB -> Replica Set
  - Transaction management is within single replica set not accross multiple replica sets.
- Casandra -> Partition
  - Transaction management is possible only if in the same partition only.
- Redundancy is not a problem then use NoSQL otherwise RDBMS.
