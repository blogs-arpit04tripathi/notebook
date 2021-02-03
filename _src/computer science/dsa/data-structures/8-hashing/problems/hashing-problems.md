---
layout: post
title: Hashing Questions
permalink: /ds/hashing/problems
---

**report all pairs**

```
Input - { {1,3},{2,6},{3,5},{7,4},{5,3},{8,7}}
Output - {3,5} and {5,3}
```

- With hashing, can be solved in single scan
- Insert each pair as key, value in hashMap.
- While insert check if value is present as existing key and key is corresponding value in the entry.

**Two Sets A and B, pair for sum K?**
- Create hashSet for A.
- Iterate over B, check hashSet for K-element.
- Time - O(Max(m,n))
- Space - O(Min(m,n))

**First repeated or non-repeated character in string**
- use frequency map (hashmap)

**Million of lines, only 2 lines are identical**

Statement - We have a file with millions of lines of data. Only two lines are identical; the rest are unique. Each line is so long that it may not even fit in the memory. What is the most efficient solution for finding the identical lines?

Solution
- Since a complete line may not fit into the main memory, read the line partially and compute the hash from that partial line.
- Then read the next part of the line and compute the hash. This time use the previous hash also while computing the new hash value.
- Continue this process until we find the hash for the complete line.
- Do this for each line and store all the hash values in a file [or maintain a hash table of these hashes].
- If at any point you get same hash value, read the corresponding lines part by part and compare.