---
layout: post
title: Binary Tree Search
permalink: /:collection/cs/ds/btree/search
---

- TOC
{:toc}

<hr><br>

# Find in Binary Tree

```java
public static boolean findinBTree(BTreeNode root, int data){
    if(root == null)
        return false;
    if(root.data == data)
        return true
    return findinBTree(root.left, data) || findinBTree(root.right, data);
}
```

# max in Binary Tree

```java
public int maxInBTree(BTreeNode node){
    int max = Integer.MIN_VALUE;
    if(root != null){
        int leftMax = maxInBTree(root.left);
        int rightMax = maxInBTree(root.right);
        max = leftMax>rightMax ? leftMax : rightMax;
        if(root.data > max)
            max=root.data;
    }
    return max;
}
```