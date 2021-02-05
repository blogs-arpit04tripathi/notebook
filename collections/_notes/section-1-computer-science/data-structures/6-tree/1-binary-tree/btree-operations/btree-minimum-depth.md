---
layout: post
title: Binary Tree Minimum Depth
permalink: /:collection/cs/ds/btree/minimum-depth
---

- Minimum depth is the depth of first leaf node in the level order traversal.

```java
public static int minimumDepth(Node root) {
    if(root == null)
        return 0;
    Queue<BTreeNode> q = new LinkedList<>();
    q.offer(root);
    q.offer(null);
    int levelDepth = 0;
    while(!q.isEmpty()){
        BTreeNode temp = q.poll();
        if(temp != null){
            if(isLeaf(temp))
                return levelDepth;
            if(temp.left !=null)
                q.offer(temp.left);
            if(temp.right !=null)
                q.offer(temp.right);
        } else {
            if(!q.isEmpty()){}
                levelDepth++;
                q.offer(null);
            }
        }
    }
    return levelDepth;
}

private static boolean isLeaf(BTreeNode root){
    return root.left==null && root.right==null;
}
```