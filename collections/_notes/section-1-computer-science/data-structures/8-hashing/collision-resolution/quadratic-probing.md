---
layout: post
title: Quadratic probing
permalink: /:collection/cs/ds/hashing/quadratic-probing
---

- The problem of Clustering can be reduced if we use the quadratic probing method.
- we start from the original hash location i.
  - If a location is occupied, we check the locations i + 12 , i +22, i + 32, i + 42...
  - We wrap around from the last table location to the first table location if necessary.
- `rehash(key) = (n+k^2) % tableSize`
- Even though clustering is avoided by quadratic probing, still there are chances of clustering.
- Both linear and quadratic probing use a probing sequence that is independent of the search key.

![]({{site.cdn}}/cse/ds/hashing/quadratic-probing.png)
