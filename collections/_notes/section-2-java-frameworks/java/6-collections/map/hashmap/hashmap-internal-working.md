---
layout: post
title: HashMap Internal Working
permalink: /:collection/java/collections/hashmap-internal-working
---

- TOC
{:toc}

<hr><br>

![hashmap-internal]({{site.cdn}}/java/collections/hashmap-internal.png)

# Bucket
* A ***bucket/segment*** is used to store key value pairs.
* A bucket can have multiple key-value pairs. 
* In hash map, bucket uses simple linked list to store objects.
* It is not a LinkedList as in a `java.util.LinkedList` - It's a separate (simpler) implementation just for the map.

# get(Key k)
* key is null, then hash and index both are 0.
* key not null, key.hashCode() passed to static hash function to find a bucket location(backing array) ie. index. 
* ***both key and value is stored in the bucket as a form of Entry object.***
* ***Entry object stores in the bucket like this (hashcode, key, value, next).***
* traverse through linked list, keys.equals() until it return true. Return value of corresponding entry object.

```java
Public V get(Object key) {
     if (key ==null)
     // Some code    
     int hash = hash(key.hashCode());    
     // if key found in hash table then return value
     // else return null
}
```

#### Why calculate hashvalue again using hash(hashValue) 
* hashCode gives an int that may be out index range, do modulo hashing.  

# put()
**When an element is added / retrieved, same procedure follows**:
* Using key.hashCode(), determine initial hashvalue for the key.
* Pass intial hashvalue as hashValue in hash(hashValue) function, to calculate the final hashvalue.
* Final hash value is then passed as a first parameter in the indexFor(int ,int) method.  The second parameter is length which is a constant in HashMap Java Api, represented by **DEFAULT_INITIAL_CAPACITY**(default 16).
* indexFor(int,int) method returns the first entry in the appropriate bucket.
* The linked list in the bucket is then iterated over - (the end is found and the element is added or the key is matched and the value is returned)

```java
/*Returns index for hash code h.*/
static int indexFor(int h, int length) {   return h & (length-1);  }
```
* The above function indexFor() works because Java HashMaps always have a capacity, i.e. number of buckets, as a power of 2.

### Example
* capacity 256, 0x100, but it could work with any power of 2.
* Subtracting 1 from a power of 2 yields the exact bit mask needed to bitwise-and with the hash to get the proper bucket index, of range 0 to length - 1.

```java
256 - 1 = 255
0x100 - 0x1 = 0xFF
E.g. a hash of 257 (0x101) gets bitwise-anded with 0xFF to yield a bucket number of 1.
```

**How will you measure the performance of HashMap?**  
* capacity     - default 16
* load factor     - default 0.75
* `number of entries > (load factor) x (current capacity)`, hash table is rehashed to have twice the number of buckets.

time complexity of Hashmap get() and put()
– due to hashing O(1), buckets have specified.

**How do you use a custom object as key in Collection classes like HashMap?**  
* ***Override equals() and hashCode()*** method to fulfill the contract.
* If not implemented correctly, it will result in two keys producing the same hashCode() and equals() output.
  * This causes unexpected overwrite of key-value pair.
* For SortedCollections (SortedMap), make sure that ***equals() is consistent to compareTo()***.
  * If inconsistent, then collection will not follow their contracts, that is, Sets may allow duplicate elements.

# HashMap Improvement in Java 8
* when a bucket becomes too big (TREEIFY_THRESHOLD = 8), ***HashMap dynamically replaces it with an ad-hoc implementation of tree map***. 
* Now, rather than O(n) we get O(logn) due to Tree data structure for the bucket. 
* HashMap promotes list into ***binary tree, using hashCode() as a branching variable***. 
* In a bucket to be transformed to Red Black Tree,
	- If two hashes are different, bigger hashcode becomes right child.
	- If hashes are equal,
		- HashMap hopes keys to be Comparable and establish some order. (not a requirement, but a good practice).
		- If keys are not comparable, don't expect any performance improvements in case of heavy hash collisions.

**When and how does HashMap convert the bucket from linked list to Red Black Trees?**  
* single bucket will be transformed to a ***perfectly balanced red black tree node***.
	- single bucket has ***at least 8 entries (TREEIFY_THRESHOLD)***
	- total number of buckets is ***more then 64 buckets (MIN_TREEIFY_CAPACITY)*** 
* Shrinkage happens when you remove entries, ***UNTREEIFY_THRESHOLD == 6***
* Keys should be Comparable - but that is not always required, it is good if they are (in case they have the same hashCode), but in case they are not, below tieBreakOrder() is used:

```java
static int tieBreakOrder(Object a, Object b) {
  int d;
  if (a==null || b==null || (d=a.getClass().getName().compareTo(b.getClass().getName()))==0)
    d = (System.identityHashCode(a)<=System.identityHashCode(b)?-1:1);
  return d;
}
```
So the className as a String is used for comparison and if that fails too, then System.identityHashCode is used (Marsaglia XOR-Shift algorithm) to decide the left and right.

***When does this conversion happen?***
* When resize of your HashMap is required, ***number of buckets increases by a factor of 2***.
* or when a certain ***bucket is transformed to a tree***.

This process of converting LinkedList to Red Black Tree is pretty slow
* Java HashMap is "sloooooooow, then is fast fast fast; then it's sloooooo, then it's fast fast fast" (There are PauselessHashMap implementations).

This brings two interesting points:
* Choose correct size of your Map initially in order to avoid some resize cycles. (new HashMap<>(256);)
* Why transforming to a Tree is important (think database indexes and why they are B-Tree...).
  * How many steps it would take you to find an entry in a perfect tree that has INTEGER.MAX_VALUE entries (theoretically). Only up to 32.

# remove()
* find the desired Entry object for removal - hashValue, key and bucketindex.
* remove(key) - calls removeEntryForKey(key) method  internally, which calculate the final hashValue of the key object.
* hashValue is passed in the indexFor(int,int) method to find the first entry object in the appropriate bucket.
* bucket(var table) is a LinkedList effectively, start traversal from object returned by indexFor(int,int). 
* if .eqauls() return true for a key during traversal, removed that single entry object from the LinkedList. 
* local variable e contains the Entry returned by removeEntryForKey(key) method.

```java
If(e==null) 
  return null
else
  return value of removed Entry object.
```
time complexity remove(key)
* Best Case time complexity of remove(key)  : O(1)  
* Worst Case time complexity of remove(key) : O(n)

**removeEntryForKey(key) has recordRemoval() concrete method without any body, what’s the use?**  
* empty concrete method `recordRemoval()` is invoked whenever the Entry is removed from the table. 
* Since LinkedHashMap extends HashMap, it is overridden in LinkedHashMap's Entry to maintain its linked list of entries.

![hashmap]({{site.cdn}}/java/collections/hashmap.png)
