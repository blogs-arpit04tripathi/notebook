---
layout: post
title: Double hashing
permalink: /:collection/cs/ds/hashing/double-hashing
---

- Double hashing reduces clustering in a better way. 
- The increments for the probing sequence are computed by using a second hash function.
- If the location is occupied, we probe the location h1(key) + h2(key), h1(key) + 2 * h2(key), 

![]({{site.cdn}}/cse/ds/hashing/double-hashing.png)