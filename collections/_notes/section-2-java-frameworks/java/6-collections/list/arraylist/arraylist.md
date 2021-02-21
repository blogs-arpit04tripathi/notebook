---
layout: post
title: ArrayList class
permalink: /:collection/java/collections/arraylist
---

* **ArrayList** - dynamic array, increase or decrease in size.
* ***Dynamic arrays*** are also supported by the legacy class Vector 
* **Capacity**: Size of arrayList, number elements it can hold.
* **ensureCapacity()** - Because reallocations are costly in terms of time, preventing unnecessary ones improves performance.

```java
ArrayList( )
ArrayList(Collection<? extends E> c)
ArrayList(int capacity)
```

**Why does ArrayList use transient storage?**  
```java
private transient Object[] elementData;    // backing array declaration
```
* ArrayList class can be serialized, but by design writeObject() does not save the backing array.
* Instead, it serializes the elements (including null values) till size() limit.
* This ***avoids*** the overheads of ***serializing the unused slots at the end of the array***.
* On deserialization, a new backing array of the minimum required size is created by readObject().