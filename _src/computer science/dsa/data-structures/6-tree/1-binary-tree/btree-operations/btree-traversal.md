---
layout: post
title: Binary Tree Traversal
permalink: /ds/btree/traversal
---

- TOC
{:toc}

<hr><br>

- Process of visiting all nodes is called ***tree traversal***.
- Each node is processed only once, but maybe visited more than once.
- Traversal Possibilities : LDR - RDL, DLR - DRL, LRD - RLD.
- Classification of traversal is done based on position of D
  - DLR - preorder traversal
  - LDR - inorder traversal
  - LRD - postorder traversal
- Level Order Traversal

# Depth First Search
## Preorder Traversal

```java
// DLR
public void preOrder(BTNode root){
    if(root==null) return;
    System.out.print(root.data+" ");
    preOrder(root.left);
    preOrder(root.right);
}
```

## Inorder Traversal

```java
// LDR
public void inOrder(BTNode root){
    if(root==null) return;
    inOrder(root.left);
    System.out.print(root.data+" ");
    inOrder(root.right);
}
```

## Postorder Traversal

```java
// LRD
public void postOrder(BTNode root){
    if(root==null) return;
    postOrder(root.left);
    postOrder(root.right);
    System.out.print(root.data+" ");
}
```

# Breadth First Search
## Level Order Traversal

**Pseudo Code**
```
1. Keep a queue for level nodes.
2. add to queue - root and null (represents level end).
3. read from queue till empty, on each read add left and right child from next level (l+1).
4. on reading null, if queue is not empty then add null to queue to mark new level end.
```

Last Node processed from the queue in Level Order Traversal is the **Deepest Node in the binary tree**.

**Implementation - Return All Levels**
```java
public ArrayList<ArrayList<Integer>> levelOrder(BTNode root){
    ArrayList<ArrayList<Integer>> levels = new ArrayList<>();
    if(root==null)
        return levels;
    Queue<BTNode> q = new LinkedList<>();
    q.offer(root);
    q.offer(null);
    ArraysList<Integer> curr = new ArrayList<>();
    while(!q.isEmpty()){
        BTNode temp = q.poll();
        if(temp == null){
            // level ended - push curr level to levels
            levels.add(new ArrayList<Integer>(curr));
            curr.clear();
            if(!q.isEmpty())
                q.offer(null);
        } else {
            curr.add(temp);
            if(temp.left != null) q.offer(temp.left);
            if(temp.right != null) q.offer(temp.right);
        }
    }
    return levels;
}
```
**Implementation - Only Print**
```java
public static void levelOrder(Node root) {
  if(root==null) return;
  Queue<Node> q = new LinkedList<>();
  q.offer(root);
  while(!q.isEmpty()){
      Node curr = q.poll();
      System.out.print(curr.data+ " ");
      if(curr.left != null) q.offer(curr.left);
      if(curr.right != null) q.offer(curr.right);
  }
}
```

```java
import java.util.*;
public static int height(Node root) {
  	if(root==null || isLeaf(root)) return 0; // single node h = 0
    return 1 + Math.max(height(root.left), height(root.right));
}

public static boolean isLeaf(Node root){
    return root.left==null && root.right==null;
}
```