---
layout: post
title: Stateless and Stateful Operations
permalink: /:collection/java/java8/streams/operations/stateless-stateful
---

**What are Stateless and Stateful operations in Java stream?**  
Intermediate operations are further divided into stateless and stateful operations.
* ***Stateless operations***, such as filter and map, retain no state from previously seen element when processing a new element, each element can be processed independently of operations on other elements.
* ***Stateful operations***, such as distinct and sorted, may incorporate state from previously seen elements when processing new elements. Stateful operations may need to process the entire input before producing a result. For example, one cannot produce any results from sorting a stream until one has seen all elements of the stream.
