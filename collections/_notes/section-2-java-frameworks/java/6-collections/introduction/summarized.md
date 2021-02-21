---
layout: post
title: Collections Summarized
permalink: /:collection/java/collections/summarized
---

|collection|Base class|Base interfaces|Duplicate|Ordered|Sorted|Thread-safe|
|---|---|---|---|---|---|---|
|ArrayList\<E>|AbstractList\<E>|List\<E>|Yes|Yes|No|No|
|LinkedList\<E>|AbstractSequentialList\<E>|List\<E><br>Deque\<E>|Yes|Yes|No|No|
|Vector\<E>|AbstractList\<E>|List\<E>|Yes|Yes|No|Yes|
|HashSet\<E>|AbstractSet\<E>|Set\<E>|No|No|No|No|
|LinkedHashSet\<E>|HashSet\<E>|Set\<E>|No|Yes|No|No|
|TreeSet\<E>|AbstractSet\<E>|Set\<E><br>NavigableSet\<E><br>SortedSet\<E>|No|Yes|Yes|No|
|Hashtable\<K, V>|Dictionary\<K, V>|Map\<K, V>|No|No|No|Yes|
|HashMap\<K, V>|AbstractMap\<K, V>|Map\<K, V>|No|No|No|No|
|LinkedHashMap\<K, V>|HashMap\<K, V>|Map\<K, V>|No|Yes|No|No|
|TreeMap\<K, V>|AbstractMap\<K, V>|Map\<K, V><br>NavigableMap\<K, V><br>SortedMap\<K, V>|No|Yes|Yes|No|

* All lists allow duplicate elements which are ordered by index. All list elements are not sorted.
* All sets and maps do not allow duplicate elements.
* Generally, sets and maps do not sort its elements, except **TreeSet** and **TreeMap** – which sort elements by natural order or by a comparator.
* Generally, elements within sets and maps are not ordered, except **LinkedHashSet** and **LinkedHashMap** - elements ordered by insertion order.
- There are only two collections are thread-safe: **Vector** and **Hastable**. The rest is not thread-safe.
