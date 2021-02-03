---
layout: post
title: Comparisons - Open Addressing methods
permalink: /ds/hashing/open-addressing-comparision
---

|Linear Probing|Quadratic Probing|Double Hashing|
|---|---|---|
|Fastest among 3|Easiest to implement and deploy|Makes more efficient use of memory|
|Uses Few Probes|Uses extra memory, doesn't probe all locations in hash table|Uses fewer probes but takes more time.|
|Problem - Primary Clustering|Problem - Secondary Clustering|More complicated to implement|
|Fixed probe interval = 1|Interval between probes increases quadratically.|Interval between probes calculated ny another hash function|