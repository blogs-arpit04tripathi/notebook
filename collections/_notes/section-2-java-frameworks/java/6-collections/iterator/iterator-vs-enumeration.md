---
layout: post
title: Iterator vs Enumeration
permalink: /:collection/java/collections/iterator-vs-enumeration
---

|Iterator						|Enumerator	|
|---							|---		|
|has remove() method			|			|
|Fail-Fast						|Fail-Safe	|
|throws ConcurrentModificationException if a Collection is modified while iterating other than its own remove() method|doesn’t throw ConcurrentModificationException if Collection is modified during the traversal.|
|New Interface					|Legacy Interface|
|ArrayList, LinkedList, HashSet, LinkedHashSet, TreeSet, HashMap, LinkedHashMap, TreeMap etc.|Vector, HashTable and Stack|
|hasNext(), next(), remove()	|hasMoreElements(), nextElement()	|
|			|twice as fast as Iterator	|
|			|uses very less memory|