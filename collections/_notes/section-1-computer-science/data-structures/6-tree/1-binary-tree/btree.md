---
layout: post
title: Binary Tree
permalink: /:collection/cs/ds/btree/
---

- TOC
{:toc}

<hr>

# Introduction to Trees

- Non-Linear data structure.
- way of representing the hierarchical nature of a structure.
- order of the elements is not important.
- Recursive Data Structure.

![](https://github.com/arpit04tripathi/files-cdn/raw/cdn/dsa/ds/tree/btree/binary-tree.png)

# Terms Used
- **root** - supernode of the tree ie. node without a parent.
- **edge** - link from parent to child.
- **leaf** - no children.
- **children** - 
- **parent** - 
- **sibling** - children of same parent
- **grandparent** -
- **ancestor** - `root -> ancestor -> descendent`, ancestor in path from root to descendent.
- **descendent** - 
- **Depth** - Length of path from root to node ie. number of edges in the path. 
- **Height** - Number of edges in longest path from node to leaf. root has height 0.
- **level** - set of all nodes at given depth. root is at level 0.

Note: for a tree `height == depth` always. It differs only for the individual nodes.

# Applications
- Storing naturally hierarchical data - file systems.
- Dictionary - Trie
- Network Routing Algorithms
- JavaScript Document Object Model considers HTML page as a tree with nesting of tags as parent child relations.
- Expression trees are used in compilers.
- Huffman coding trees that are used in data compression algorithms.
- Binary Search Tree (BST) - O(logn) (average) search, insertion and deletion.
- Priority Queue (PQ) - log(n) (in worst case) search and deletion of minimum (or maximum).

# Types of Tree
- BTree - Binary Tree
- BST - Binary Search Tree
- Heap Tree
- AVL Tree
- Red Black Tree
- Syntax Tree
- Huffman Coding Tree

# Binary Tree
- At most two children.
- Empty tree if root is null.
- **Depth First Traversal** : Inorder (Left-Root-Right), Preorder (Root-Left-Right) and Postorder (Left-Right-Root)
- **Breadth First Traversal** : Level Order Traversal

# Modifiable Collection

|           |Search(x)  |Insert(x)  |Delete(x)  |
|---        |---        |---        |---        |
|Array      |O(n)       |O(1) / O(n)|O(n)       |
|LinkedList |O(n)       |O(1) - head|O(n)       |
|Tree (BST) |O(log(n))  |O(log(n))  |O(log(n))  |
