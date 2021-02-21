---
layout: post
title: NavigableMap Interface Methods
permalink: /:collection/java/collections/navigable-map-interface-methods
---

|NavigableMap Interface					|	|
|---									|---|
|Map.Entry<K,V> firstEntry( )			|
|Map.Entry<K,V> lastEntry( )			|
|K firstKey( )							|
|K lastKey( )							|
|SortedMap<K, V> tailMap(K start)		|
|SortedMap<K, V> headMap(K end)			|				
|SortedMap<K, V> subMap(K start, K end)	|
|NavigableMap<K,V> headMap(K upper, boolean incl)		|
|NavigableMap<K,V> tailMap(K lowerBound, boolean incl)	|
|NavigableMap<K,V> subMap(K lower, boolean lowIncl, K upper, boolean highIncl)|
|Comparator<? super K> comparator( )	|
|Map.Entry<K,V> ceilingEntry(K obj)		|smallest k >= obj
|K ceilingKey(K obj)					|smallest k >= obj
|Map.Entry<K,V> floorEntry(K obj)		|largest k <= obj.
|K floorKey(K obj)						|largest k <= obj.
|Map.Entry<K,V> higherEntry(K obj)		|smallest k > obj
|K higherKey(K obj)						|smallest k > obj				|
|Map.Entry<K,V> lowerEntry(K obj)		|largest k < obj	
|K lowerKey(K obj)						|largest k < obj.				|
|NavigableMap<K,V> descendingMap( )		|
|NavigableSet<K> descendingKeySet( )	|
|NavigableSet<K> navigableKeySet( ) 	|
|Map.Entry<K,V> pollFirstEntry( ) 		|
|Map.Entry<K,V> pollLastEntry( ) 		|
