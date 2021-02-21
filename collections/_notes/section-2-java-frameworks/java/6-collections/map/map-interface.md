---
layout: post
title: Map Interface
permalink: /:collection/java/collections/map-interface
---


* **Map** – stores data as key/value pairs. 
* Map<K, V>
  * K specifies the type of keys
  * V specifies the type of values.
* Some maps can accept a **null** key and null values, others cannot.
* not **Iterable**, can’t obtain iterator to a map.

|	|	|
|---|---|
|Map 			|Maps unique keys to values.|
|Map.Entry 		|inner class of Map. Defines element as key-value pair.|
|SortedMap 		|keys are maintained in ascending order|
|NavigableMap	|Extends SortedMap to handle the retrieval of entries based on closest-match searches.|

**Why Map interface doesn’t extend Collection interface?**  
* Map doesn’t fit into the “group of elements” paradigm.
* Map contains key-value pairs and it provides methods to retrieve list of Keys or values as Collection.
* By getting a collection-view, maps are integrated into the larger Collections Framework.
	- **entrySet( )** - returns a Set that contains the elements in the map.
	- **keySet( )** - To obtain a collection-view of the keys.
	- **values( )** - To get a collection-view of the values.
