---
layout: post
title: BTree Level Order - Print levels bottom up
permalink: /ds/btree/level-print-bottom-up
---

- Level Order
  - input - `1` `2 3` `4 5 6 7`
  - output - `4 5 6 7` `2 3` `1`
- Do a level order Traversal, offer right child first in the q and then left child. push to stack during poll. Print the stack when queue is empty.

```java
public static void levelOrderTraversalInReverse(BTreeNode root){
    if(root == null)
        return;
    Stack<BTreeNode> stack = new Stack<>();
    Queue<BTreeNode> q = new LinkedList<>();
    q.offer(root);
    while(!q.isEmpty()){
        BTreeNode temp = q.poll();
        if(temp.right != null)
            q.offer(temp.right);
        if(temp.left != null)
            q.offer(temp.left);
        s.push(temp);
    }
    while(!s.isEmpty())
        System.out.println(s.pop().data + "");
}
```