---
layout: post
title: Remove Duplicate from character array
permalink: /:collection/cs/ds/hashing/remove-duplicate-char
---

# Brute Force
- Time - O(n2)
- Space - O(1)
- Take each character and compare with all the later characters

```java
public static void main(String[] args) {
    char str[] = "geeksforgeeks".toCharArray();
    int n = str.length;
    System.out.println(removeDuplicate(str, n));
}

static String removeDuplicate(char str[], int n) {
    int index = 0;
    for (int i = 0; i < n; i++) {
        int j;
        for (j = 0; j < i; j++)
            if (str[i] == str[j])
                break;
        // If not present, then add it to result. 
        if (j == i)
            str[index++] = str[i];

    }
    return String.valueOf(Arrays.copyOf(str, index));
}
```
```
geksfor
```

# Sort to bring repeated characters
- Time - O(n logn)
- Space - O(1)

```java
public static void main(String[] args) {
    char str[] = "geeksforgeeks".toCharArray();
    Arrays.sort(str);
    int n = str.length;
    System.out.println(removeDuplicate(str, n));
}

static String removeDuplicate(char str[], int n) {
    int index = 0;
    for (int i = 1; i < n; i++) {
        if (str[i] == str[index]) {
            continue;
        }
        str[++index] = str[i];
    }
    return String.valueOf(Arrays.copyOf(str, index + 1));
}
```
```
[e, e, e, e, f, g, g, k, k, o, r, s, s]
[e, f, g, k, o, r, s, k, k, o, r, s, s]
efgkors
```

# Use HashSet (Internally uses HashMap) - Hashing
- Time - O(n)
- Space - O(n)

```java
public static void main(String[] args) {
    char str[] = "geeksforgeeks".toCharArray();
    int n = str.length;
    System.out.println(removeDuplicate(str, n));
}

static String removeDuplicate(char str[], int n) {
    Set<Character> hashset = new HashSet<>();
    int index = 0;
    for (int i = 0; i < n; i++) {
        if (hashset.contains(str[i])) {
            continue;
        } else {
            hashset.add(str[i]);
            str[index++] = str[i];
        }
    }
    return String.valueOf(Arrays.copyOf(str, index));
}
```