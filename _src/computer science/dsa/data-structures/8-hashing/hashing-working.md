---
layout: post
title: Hashing - How it works
permalink: /ds/hashing/understanding
---

**Print the first repeated character**
- Brute Force - Take each character and compare with all other chars to find if duplicate.
  - O(n2) - time complexity
  - O(1) - space complexity
- Better Solution - remember the previous characters in some array
- In simple terms we can treat array as a hash table.
  - number of possible characters is 256 (for simplicity assume ASCII characters only).
  - For each of the input characters go to the corresponding position and increment its count.

```java
int count[] = new int[256];
for(int i=0; i<str.length i++){
	if(count[str[i]] == 1){
		System.out.println(str[i]);
		break;
	} else{
		count[str[i]]++;
	}
}
System.out.println("No repeated characters");
```

**Why HashTable, Why not Arrays?**
- In the previous problem, we know the number of different possible characters (256) in advance.
- Suppose the given array has numbers instead of characters, set of possible values is infinity (or at least very big).
- The process of mapping the keys to locations is called ***hashing***.
- simple function is `key % table size`.

![](https://github.com/arpit04tripathi/files-cdn/raw/cdn/dsa/ds/hashing/why-hashing.png)
