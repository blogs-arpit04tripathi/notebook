---
layout: post
title: SINGLE_TABLE Strategy (Table Per Hierarchy)
permalink: /:collection/hibernate/table-per-hierarchy
---

This is default, even if no @Inheritance is noted on Vehicle class.  
Even if Vehicle, TwoWheeler and FourWheeler are implemented as separate @Entity, these are not mapped as separate tables. It has mapped everything to base class Vehicle with DTYPE recording the class name.

**DTYPE – Discriminator Type**

![inheritance-single-table-dtype]({{site.cdn}}/hibernate/inheritance-single-table-dtype.png)

```java
@Entity
@Inheritance(Strategy=InheritanceType.SINGLE_TABLE)
@DiscriminatorColumn(name="VEHICLE_TYPE", DiscriminatorType.STRING)
Public class Vehicle{ }

@Entity
@DiscriminatorValue("Bike")
Public class TwoWheeler{ }
```
```
DiscriminatorType.STRING
DiscriminatorType.INTEGER
DiscriminatorType.CHAR
```

Note:  Discriminator is needed only for Single Class Strategy

# Advantages of Single Table Strategy
-	Simplest to implement.
-	Only one table to deal with.
-	Performance wise better than all strategies because no joins or sub-selects need to be performed.

# Disadvantages of Single Table Strategy
-	Most of the column of table are nullable so the NOT NULL constraint cannot be applied.
-	Tables are not normalized.

