---
layout: post
title: JOINED Strategy (Table Per Subclass)
permalink: /hibernate/table-per-subclass
---

```java
@Entity
@Inheritance(Strategy=InheritanceType.JOINED)
Public class Vehicle{ }
```

![](https://github.com/arpit04tripathi/files-cdn/raw/cdn/hibernate/inheritance-table-per-subclass.png)

# Advantages of Joined Table Strategy
-	Tables are normalized.
-	You can define NOT NULL constraints.

# Disadvantages of Joined Table Strategy
-	Low performance as it runs OUTER JOIN as well as INNER JOIN in select stements.

```java
@PrimaryKeyJoinColumn(name="ID")  
public class Regular_Employee extends Employee{  
```
