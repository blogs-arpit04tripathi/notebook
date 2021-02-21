---
layout: post
title: HashSet Internal Working (How Set Ensures Uniqueness)
permalink: /:collection/java/collections/hashset-internal-working
---


* ***HashMap is used internally***.
* Key/value pair where value is always null. ***<3,null>***
* Duplicate - add() return false and doesn’t add to HashSet.
* put (key,value) in the internal code will return
	- null, if key is unique and added to the map
	- Old Value of the key, if key is duplicate

```java
public class HashSet<E> extends AbstractSet<E> implements Set<E>, Cloneable, java.io.Serializable{
    private transient HashMap<E,Object> map;    
    // Dummy value to associate with an Object in the backing Map  
    private static final Object PRESENT = new Object();    
    public HashSet() { map = new HashMap<>(); }
    // SOME CODE ,i.e Other methods in Hash Set
    public boolean add(E e) { return map.put(e, PRESENT)==null; }
    // SOME CODE ,i.e Other methods in Hash Set
}
```
