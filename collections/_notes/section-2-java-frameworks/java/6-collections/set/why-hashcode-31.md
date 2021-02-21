---
layout: post
title: Why Hashcode 31?
permalink: /:collection/java/collections/why-hashcode-31
---

- The number 31 was chosen because it is a prime number. 
  - They could have chosen any other prime number. 
- Hash-based collections store elements in so-called ***buckets***. A hash-based collection has a fixed number of buckets.
  - For hash-based collection, hash code of the object determines the bucket to put the object.
  - bucketIndex = hashCode() % numberOfBuckets.
- When you want to find an object in a hash-based collection, this is what happens: 
	- ***Compute hashCode()*** of the object to find the bucket for search.
	- Check all objects in the bucket by ***equals()***.
- Weak Point: Works well if elements are evenly-distributed among the buckets.
  - should have a proper hashCode() method. 
- HashSet and HashMap in Java have a number of buckets that is normally a power of 2 (by default, a HashMap has 16 buckets, for example). 
- By making the hash code of objects a prime number (or a multiple of a prime number) the objects will be distributed better over the buckets, because a prime number is not a multiple of the number of buckets (which is a power of 2), so ***hashCode() % numberOfBuckets won't quickly cycle back to the same bucket***.