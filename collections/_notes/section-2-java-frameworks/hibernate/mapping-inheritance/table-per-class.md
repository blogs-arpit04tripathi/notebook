---
layout: post
title: TABLE_PER_CLASS Strategy (Table Per Concrete class)
permalink: /:collection/hibernate/table-per-class
---

```java
@Entity
@Inheritance(Strategy=InheritanceType.TABLE_PER_CLASS)
Public class Vehicle{ }
```

![]({{site.cdn}}/hibernate/inheritance-table-per-class.png)

Here, @GeneratedValue is inherited by all the childs as well. Generated values 1,2,3.

# Advantages of Table Per Class Strategy
-	You can define NOT NULL constraints on the table.

# Disadvantages of Table Per Class Strategy
-	Tables are not normalized.
-	Select statements require more time to execute as UNION operation is applied.
