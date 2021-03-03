---
layout: post
title: Hibernate Cascading
permalink: /:collection/hibernate/cascade
---

**What is cascading and what are different types of cascading?** 
-	When we have relationship between entities, then we need to define how the different operations will affect the other entity. This is done by cascading and there are different types of it.
-	Here is a simple example of applying cascading between primary and secondary entities.

```java
import org.hibernate.annotations.Cascade;

@Entity
@Table(name = "EMPLOYEE")
public class Employee {
    @OneToOne(mappedBy = "employee")
    @Cascade(value = org.hibernate.annotations.CascadeType.ALL)
    private Address address;
}
```
-	Hibernate CascadeType enum constants are little bit different from JPA javax.persistence.CascadeType, so we need to use the Hibernate CascadeType and Cascade annotations for mappings, as shown in above example.
-	Commonly used cascading types as defined in CascadeType enum are:
    - **None**: No Cascading, it’s not a type but when we don’t define any cascading then no operations in parent affects the child.
    - **ALL**: Cascades save, delete, update, evict, lock, replicate, merge, persist. Basically everything
    - **SAVE_UPDATE**: Cascades save and update, available only in hibernate.
    - **DELETE**: Corresponds to the Hibernate native DELETE action, only in hibernate.
    - **DETATCH**, MERGE, PERSIST, REFRESH and REMOVE – for similar operations
    - **LOCK**: Corresponds to the Hibernate native LOCK action.
    - **REPLICATE**: Corresponds to the Hibernate native REPLICATE action.

# org.hibernate.annotations.Cascade
Used to define the cascading between two entity beans, used with mappings. It works in conjunction with org.hibernate.annotations.CascadeType
