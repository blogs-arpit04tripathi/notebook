---
layout: post
title: SortedMap Map Interface
permalink: /:collection/java/collections/sorted-map-interface
---

* Ascending order on keys.
  * **firstKey( )** – smallest.
  * **lastKey()** - largest.
* Several methods throw a **NoSuchElementException** when no items are in the invoking map.
* efficient manipulations of submaps. **headMap( ), tailMap( ), subMap( )**. 
* The ***submap returned*** by these methods ***is backed by the invoking map ie. Changing one changes the other***.
