---
layout: post
title: Binary Tree Size
permalink: /:collection/cs/ds/btree/size
---

```java
public static int size(BTreeNode root) {
    if(root == null)
        return 0;
    return 1 + size(root.left) + size(root.right);
}
```