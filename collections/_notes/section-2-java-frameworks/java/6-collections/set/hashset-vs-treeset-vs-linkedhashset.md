---
layout: post
title: HashSet vs TreeSet vs LinkedHashSet
permalink: /:collection/java/collections/hashset-vs-treeset-vs-linkedhashset
---


|					          |HashSet	|LinkedHashSet|TreeSet          |
|---				        |---		  |---			    |---				      |
|**Ordering**		    |Random		|Insert Order	|Sorted			      |
|**Null Key**		    |One		  |One			    |No					      |
|**Null Value**		  |Any		  |Any			    |No					      |
|**Performance**	  |O(1)		  |O(n)			    |O(Log(n))			  |
|**implementation**	|Hashmap	|Hashmap		  |NavigableTreeMap	|
|**Comparision**	  |equals()	|equals()		  |compareTo()		  |
|**Algorithm**	 	  |			    |				      |Red-Black tree		|

```java
public TreeSet(Comparator c)
```

- `comparator.compare` method is preferred over `Comparable.compareTo()`

# Similarities between HashSet and TreeSet
* unique elements
* shallow clone
* not thread safe
* fail-fast iterators

# When to prefer TreeSet over HashSet?
* Sorted unique elements are required instead of unique elements.
  * Default - ascending order
* When one need to perform read/write operations frequently
* TreeSet has greater locality than HashSet.
* In case data needs to be read from hard drive than prefer TreeSet as it has greater locality than HashSet.
