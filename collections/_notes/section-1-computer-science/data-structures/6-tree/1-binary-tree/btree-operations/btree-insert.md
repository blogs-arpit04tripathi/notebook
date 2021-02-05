---
layout: post
title: Binary Tree Insert
permalink: /:collection/cs/ds/btree/insert
---

- For Binary Tree, order is not important.
- Insert the element ***wherever*** we find ***left or right child as null***.
- ***Can also be by level order traversal***. (bfs)

# Level Order

```java
public void insertInBTree(BTreeNode root, int data){
    if(root == null)
        return new BTreeNode(data);
    Queue<BTreeNode> q = new LinkedList<>();
    q.offer(root);
    while(!q.isEmpty()){
        BTreeNode temp = q.poll();
        if(temp.left == null)
            root.left = new BTreeNode(data);
        else if(root.right == null)
            root.right = new BTreeNode(data);
    }
    return root;
}
```

# Recursive

```java
public static BTreeNode insert(BTreeNode root,int data) {
    if(root == null)
        return new BTreeNode(data);
    else
        insertHelper(root, data);
    return root;
}

private static void insertHelper(BTreeNode root, int data){
    if(data < root.data){
        // insert in left
        if(root.left == null)
            root.left = new BTreeNode(data);
        else
            insertHelper(root.right, data);
    } else {
        //insert in right
        if(root.right == null)
            root.right = new BTreeNode(data);
        else
            insertHelper(root.left, data);
    }
}
```