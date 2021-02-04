---
layout: post
title: Components of Hashing
permalink: /ds/hashing/components
---

- TOC
{:toc}

<hr><br>

# Hash Table
- **Direct Addressing**
  - Hash table is a generalization of array.
  - Direct addressing is applicable when we can afford to allocate an array with one position for every possible key.
  - we find the element whose key is k by just looking in the kth position of the array. 
- **Hash Table**
  - If we have less locations and more possible keys, then simple array implementation is not enough.
  - Hash table or hash map is a data structure that stores the keys and their associated values
    - hash table uses a hash function to map keys to their associated values.
  - An array storing pointers to records with a specific hashcode value.
    - An entry in hash table is NIL if no existing hashcode has value equal to the index.

# Hash Function
- Used to transform the key into the index.
- **perfect hash function** - maps each item into a unique slot.
- Example - if the elements were nine-digit Social Security numbers, this method would require almost one billion slots. If we only want to store data for a class of 25 students, we will be wasting an enormous amount of memory.
- A good hash function should have following properties:
- **folding method** for constructing hash functions
  - begins by dividing the elements into equalsize pieces (the last piece may not be of equal size).
  - example - phone number element 436-555-4601 is taken in group of 2 (43,65,55,46,01). After the addition, 43+65+55+46+01, we get 210. Then perform modulo hash function.

**Characteristics of Good Hash Functions**
- Distribute key values evenly in the hash table
- Be easy and quick to compute, return value within range of locations in hash table.
- Minimize collision
- Use all the information provided in the key
- efficient collision resolution algorithm to compute an alternative index for a key.
- Have a high load factor for a given set of keys

# Load Factor
-  decision parameter used when we want to rehash or expand the existing hash table entries.
-  `load factor = number of items stored / size of the table`
-   helps us in determining the efficiency of the hashing function.
    -   It tells whether the hash function is distributing the keys uniformly or not.

# Collision
- condition where two records are stored in the same location.
- hash function gives same output for 2 different keys.

# Collision Resolution Techniques
- process of finding an alternate location is called collision resolution.
- **Direct Chaining** : An array of linked list application
  - Separate chaining
- **Open Addressing** : Array-based implementation
  - Linear probing (linear search)
  - Quadratic probing (nonlinear search)
  - Double hashing (use two hash functions)