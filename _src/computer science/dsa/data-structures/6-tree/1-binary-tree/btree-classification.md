---
layout: post
title: Binary Tree Classifications
permalink: /ds/btree/classification
---

![](https://github.com/arpit04tripathi/files-cdn/raw/cdn/dsa/ds/tree/btree/btree-classification.png)

|Classification||
|---|---|
|Binary Tree|each node can have at-most 2 children.|
|Strict/Proper BT|each node have 0 or 2 children.|
|Perfect Binary Tree|All levels are completely filled, all leafs are at the same level.|
|Complete Binary Tree|every level, except possibly the last, is completely filled, and all nodes are as far left as possible.|

# Full v.s. Complete Binary Trees

![full-complete-perfect](https://github.com/arpit04tripathi/files-cdn/raw/cdn/dsa/ds/tree/btree/full-complete-perfect.png)

* In a Full Binary, number of leaf nodes is number of internal nodes plus 1

```
L = I + 1
```

# Properties of Binary Tree
**Max number of Nodes**
```
for level h = 2^h
for full binary tree = 2^(h+1) - 1 = (2^0 + 2^1 + .... + 2^h)
for complete binary tree = 2^h to 2^(h+1)-1
```
**height**
```
h = log2(n+1) - 1
h(Complete BT) = floor(log2(n))
h(empty tree) = -1;
h(Single node tree) = 0;

For n nodes,
min height = floor(log2(n)) --> O(log2(n)) ~ O(h)
Minimum possible height     --> ceil(log2(n+1))
max height = n-1            --> O(n)        Skew Tree
```
**Leaf Nodes**
```
count(leaf nodes) = 1 + count(nodes with 2 children)
```
***Cost of operations on Binary Tree are dependent on Height of the Binary Tree.***