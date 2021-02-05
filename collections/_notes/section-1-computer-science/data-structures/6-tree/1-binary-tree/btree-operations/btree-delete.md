---
layout: post
title: Binary Tree Delete
permalink: /:collection/cs/ds/btree/delete
---

**Pseudo Code**
```
- Starting at root, find node to be deleted.
- Find deepest node.
- Swap data between them.
- delete the deepest node.
```

***Implement TODO***

```java
public static int deleteInBTree(BTreeNode root, int data){
    if(root == null)
        return Integer.MIN_VALUE;
    BTreeNode target, deepest;
    Queue<BTreeNode> q = new LinkedList<>();
    q.offer(root);
    q.offer(null);
    while(!q.isEmpty){
        BTreeNode temp = q.poll;
        if(temp != null){
            deepest = temp;
            if(temp.data == data)   target = temp;
            if(temp.left!=null)     q.offer(temp.left);
            if(temp.right!=null)    q.offer(temp.right);
        } else {
            if(!q.isEmpty())    q.offer(null);
        }
    }
    if(target == null) return Integer.MIN_VALUE;
    target.data = deepest.data;
    deepest = null; // TODO: Delete deepest
    return data;
}
```