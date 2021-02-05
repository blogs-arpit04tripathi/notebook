---
layout: post
title: Binary Tree Structurally Identical
permalink: /:collection/cs/ds/btree/structurally-identical
---

- Structurally Identical doesn't mean that they have same data.

```java
public boolean checkStructurallyIdentical(BTreeNode root1, BTreeNode root2) {
    if(root1 == null && root2 == null)  return true;
    if(root1 == null || root2 == null)  return false;
    return checkStructurallyIdentical(root1.left, root2.left) && checkStructurallyIdentical(root1.right, root2.right);
}
```