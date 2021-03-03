---
layout: post
title: Caching Strategies
permalink: /:collection/aws/elasticache/caching-strategies
---

# Lazy Loading
- Lazy Loading - Loads the data into the cache only when necessary.
- If requested data is in cache, Elasticache returns the data.
- If data not present in cache or has expired, Elasticache returns null.
- Your application then fetches the data from the DB and writes the data received into the cache so that it is available next time.

|Advantages|Disadvantages|
---|---
|Only requested data is cached: Avoids filling up cache with useless data.|Cache miss penalty: Initial request query to DB writing data to the cache.|
|Node Failures are not fatal, a new empty node will just have a lot of cache misses initially.|Stale Data - If data is only updated when there is a cache miss, it can become stale. Does't automatically update if the data in DB changes.|

### TTL for Cache
- TTL (Time To Live)
- Specifies the number of seconds until the key(data) expires to avoid keeping stale data in the cache.
- Lazy Loading treats an expired key as a cache miss and causes the application to retrieve the data from the DB and subsequently write the data into the cache with a new TTL.
- Does not eliminate stale data - but helps avoid it.

# Write Through
- Adds or updates the data to cache whenever data is written to DB.

|Advantages|Disadvantages|
---|---
|Data in cache never stales.|Write Penalty: Every write involves a write to cache as well as DB.|
|Users are generally more tolerant of additional latency when updating data than when retrieving it.|If a node fails and a new one is spun up, data is missing until added or updated in DB (mitigate by implementing Lazy Loading in conjuction with write-through)|
||Wasted resources if most of the data is never read.|

