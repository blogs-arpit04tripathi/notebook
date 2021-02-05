---
layout: post
title: Binary Tree Views
permalink: /:collection/cs/ds/btree/views
---

- TOC
{:toc}

<hr><br>

# Top View

# Bottom view

# Left View

# Right View

```java
import java.util.*;

// single node h=0
public static int minimumDepth(Node root) {
    if(root == null || isLeaf(root))
        return 0;
    return 1 + Math.max(height(root.left), height(root.right));
}

```