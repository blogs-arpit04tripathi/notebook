---
layout: post
title: EnumMap
permalink: /:collection/java/collections/enumMap
---

```java
EnumMap(Class<K> kType)
EnumMap(Map<K, ? extends V> m)
EnumMap(EnumMap<K, ? extends V> em)
```

* It is specifically for use with ***keys of an enum type***. 
* class EnumMap<K extends Enum\<K>, V>
* K must extend Enum\<K>, which enforces the requirement that the keys must be of an enum type.
