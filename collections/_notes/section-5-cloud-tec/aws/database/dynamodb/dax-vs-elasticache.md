---
layout: post
title: DAX vs Elasticache
permalink: /:collection/aws/ddb/dax-vs-elasticache
---

- DAX is optimized to only used for DynamoDB.
- DAX only supports write-through caching strategy.

In general, 
- DynamoDB - use DAX
- RDS - use Elasticache.
