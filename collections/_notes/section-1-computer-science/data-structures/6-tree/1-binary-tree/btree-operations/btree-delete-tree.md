---
layout: post
title: Binary Tree - Delete Tree
permalink: /:collection/cs/ds/btree/delete-tree
---

- To delete tree, we must traverse all the nodes and delete them.
- Which traverse to use - preorder, inorder, postorder, level order?
- Before deleting the parent node we need to delete its children nodes.
- PostOrder Traversal - does the work without storing anything.
- We can also delete tree with other traversals with extra space complexity.

```java
public void deleteBTree(BTreeNode root){
    if(root==null)
        return;
    deleteBTree(root.left);
    deleteBTree(root.right);
    root = null;
}

private boolean isLeaf(BTreeNode root){
    return root.left==null && root.right==null;
}
```

```java
public void deleteBTree(BTreeNode root){
    root = null; // garbage collector takes care of it
}
```
