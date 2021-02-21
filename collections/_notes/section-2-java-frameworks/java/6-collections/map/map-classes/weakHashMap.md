---
layout: post
title: WeakHashMap
permalink: /:collection/java/collections/weakHashMap
---

* [WeakHashMap](https://docs.oracle.com/javase/7/docs/api/java/util/WeakHashMap.html) has ***weak keys***.
* ***An entry in WeakHashMap will automatically be removed when its key is no longer in ordinary use***.
* Presence of a mapping for a given key will not prevent the key from being discarded by the garbage collector.
* It ***permits null keys and null values***.
* Not synchronized, use Collections.synchronizedMap().
* fail-fast iterator, ConcurrentModificationException will be thrown.
