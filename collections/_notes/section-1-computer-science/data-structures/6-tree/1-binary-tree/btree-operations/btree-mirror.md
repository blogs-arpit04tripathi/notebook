---
layout: post
title: Binary Tree Mirror
permalink: /:collection/cs/ds/btree/mirror
---

# Check areMirror
- left is right, right is left.

```java
public boolean areMirrors(BTreeNode root1, BTreeNode root2) {
    if(root1 == null && root2 == null)  return true;
    if(root1 == null || root2 == null)  return false;
    if(root1.data != root2.data) return false;
    return areMirrors(root1.left, root2.right) && areMirrors(root1.right, root2.left);
}
```

# Create Mirror
- bottom up approach here - first mirror left and right, then exchange left <--> right for root.

```java
public BTreeNode mirrorOfBTree(BTreeNode root) {
    if(root == null)
        return null;
    mirrorOfBTree(root.left);
    mirrorOfBTree(root.right);
    BtreeNode temp = root.right;
    root.right = root.left;
    root.left = temp;
    return root;
}
```