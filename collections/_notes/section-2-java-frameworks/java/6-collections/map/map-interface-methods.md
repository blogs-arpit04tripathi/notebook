---
layout: post
title: Map Interface Methods
permalink: /:collection/java/collections/map-interface-methods
---

|		|	|
|---|---|
|int size( )										|
|boolean isEmpty( ) 								|
|void clear( ) 										|
|int hashCode( ) 									|
|boolean equals(Object obj)							|
|Set\< Map.Entry<K, V> > entrySet( )				|
|Set\<K> keySet( ) 									|
|Collection\<V> values( )							|
|boolean containsKey(Object k)						|
|boolean containsValue(Object v)					|
|V get(Object k) 									|
|default V getOrDefault(Object k, V defVal)			|
|V put(K k, V v) 									|
|default V putIfAbsent( K k, V v)					|
|void putAll(Map<? extends K, ? extends V> m)		|
|V remove(Object k) 								|
|default boolean remove(Object k, Object v)			|
|default V replace(K k, V v)						|
|default boolean replace(K k, V oldV, V newV)		|
|default void replaceAll(BiFunction< ? super K, ? super V, ? extends V> func)|
|forEach(BiConsumer<? super K,? super V> action)	|ConcurrentModificationException
|default V merge(K k, V v, BiFunction<? super V, ? super V, ? extends V> func)			|
