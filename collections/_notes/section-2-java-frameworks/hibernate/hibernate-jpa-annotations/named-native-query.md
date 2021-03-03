---
layout: post
title: Annotation @NamedNativeQuery and @NamedNativeQueries
permalink: /:collection/hibernate/annotations/named-native-query
---

In general, you should prefer to write HQL queries because then you can let Hibernate handle the intricacies of converting the HQL into the various SQL dialects.

```java
@NamedQueries({
   @NamedQuery(name="get-emp-by-name",query="FROM EmployeeBean WHERE fName=:fName")
})
 
//Equivalent NamedNativeQuery
 
@NamedNativeQueries(
    {
        @NamedNativeQuery(
            name="get-emp-by-name-native",
            query="SELECT * FROM Employees WHERE firstName=:fName",
            resultClass=EmployeeEntity.class)
    }
)
```
