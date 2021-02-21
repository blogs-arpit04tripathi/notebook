---
layout: post
title: IdentityHashMap
permalink: /:collection/java/collections/identityHashMap
---

* It is similar to HashMap except that it uses ***reference equality when comparing elements***.
* The API documentation explicitly states that ***IdentityHashMap*** is not for general use.
* Uses [reference equality instead of object equality](https://javahungry.blogspot.com/2013/06/difference-between-equals-and-double-equals-method-with-example-java-collections-interview-question.html){:target="_blank"} when comparing keys and values.
* In IdentityHashMap two keys k1 and k2 are considered equal if only if (k1==k2).
* IdentityHashMap is not synchronized. 
* fail-fast iterator, ConcurrentModificationException will be thrown. 
