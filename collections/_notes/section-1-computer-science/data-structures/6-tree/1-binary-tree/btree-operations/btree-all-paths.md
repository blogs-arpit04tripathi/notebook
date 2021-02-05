---
layout: post
title: Binary Tree All Paths Root to Leaf
permalink: /:collection/cs/ds/btree/all-paths
---

```java
public void printPaths(BTreeNode root) {
    int[] path = new int[256];
    printPaths(root, path, 0);
}

// level acts as index, 0 is root element
private void printPaths(BTreeNode root, int[] path, int level){
    if(root==null)
        return;
    path[level] = root.data;
    level++;
    if(isLeaf(root)){
        System.out.println(Arrays.toString(path));
    } else{
        printPaths(root.left, path, level);
        printPaths(root.right, path, level);
    }
}

private boolean isLeaf(BTreeNode root){
    return root.left==null && root.right==null;
}
```