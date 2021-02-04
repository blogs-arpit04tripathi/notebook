---
layout: post
title: Array vs List
permalink: /ds/array-vs-list
---

|   |Array|List|
|---|---|---|
|Size|Fixed Size, unused memory|No unused memory, extra 4 bytes per item for pointer|
|Memory|Contiguous, may not be available for large size requirements|Sparse|
|Access|O(1)|O(n) - traverse to element|
|Insert(Head)|O(n)|O(1)|
|Insert(Tail)|O(n)|O(n)|
|Insert(Mid)|O(n)|O(n)|