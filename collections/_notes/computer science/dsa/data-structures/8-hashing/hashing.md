---
layout: post
title: Hashing
permalink: /:collection/cs/ds/hashing
---

**What is Hashing?**
- Hashing is a technique used for storing and retrieving information as quickly as possible. 
- It is used to perform optimal searches and is useful in implementing symbol tables.

**Why Hashing?**
- Balanced BST - insert, delete and search in O(logn)
- Hashing does these operations in O(1), but elements are unordered..
  - Worst case complexity is O(n), but average O(1).
- BST easier to implement as hash functions can sometimes be very complex to generate.
- In BST, we can also efficiently find floor and ceil of values.

**Use Cases**
- can be used to remove duplicates from a set of elements, find frequency of all items.
- example: 
    - in web browsers, can check visited urls using hashing. 
    - in firewalls, can use hashing to detect spam by hashing IP addresses.
    - hashing can be used in any situation where want search() insert() and delete() in O(1) time.

**HashTable ADT**
- *CreatHashTable*: Creates a new hash table
- *HashSearch*: Searches the key in hash table
- *Hashlnsert*: Inserts a new key into hash table
- *HashDelete*: Deletes a key from hash table
- *DeleteHashTable*: Deletes the hash table
