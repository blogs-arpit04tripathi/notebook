---
layout: post
title: Binary Tree Path with Sum
permalink: /:collection/cs/ds/btree/path-with-sum
---

# Print all Paths with sum (evem for intermediate nodes)
- with each step in dfs, substract sum by node data and print the path whenever sum==0.

```java
public void printPathsWithSum(BTreeNode root, int sum) {
    int[] path = new int[256];
    printPaths(root, path, 0, sum);
}

// level acts as index, 0 is root element
private void printPaths(BTreeNode root, int[] path, int level, int sum){
    if(root==null)
        return;
    path[level] = root.data;
    level++;
    sum -= root.data;
    if(sum == 0)){
        System.out.println(Arrays.toString(path));
    printPaths(root.left, path, level, sum);
    printPaths(root.right, path, level, sum);
}

private boolean isLeaf(BTreeNode root){
    return root.left==null && root.right==null;
}
```

# hasPathSum

```java
public boolean hasPathSum(BTreeNode root, int sum) {
    if(root==null) return false;
    if(isLeaf(root) && sum==root.data)
        return true;
    sum -= root.data;
    return hasPathSum(root.left, sum) || hasPathSum(root.right, sum);
}

private boolean isLeaf(BTreeNode root){
    return root.left==null && root.right==null;
}
```