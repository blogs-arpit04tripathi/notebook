---
layout: post
title: this Keyword
permalink: /:collection/java/this
---

```java
Box(double w, double h, double d) {
    this.width = w;
    this.height = h;
    this.depth = d;
}
```

* **this** - refer to the object that invoked it.
* **Instance Variable Hiding** - local variable with same name as an instance variable, hides the instance variable.