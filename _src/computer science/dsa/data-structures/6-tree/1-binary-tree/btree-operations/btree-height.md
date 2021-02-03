---
layout: post
title: Binary Tree Height
permalink: /ds/btree/height
---

```java
import java.util.*;

// single node h=0
public static int height(Node root) {
    if(root == null || isLeaf(root))
        return 0;
    return 1 + Math.max(height(root.left), height(root.right));
}

public static boolean isLeaf(Node root){
    return root.left == null && root.right == null;
}

// single node h=1
public static int height(Node root) {
    if(root == null)
        return 0;
    return 1 + Math.max(height(root.left), height(root.right));
}
```