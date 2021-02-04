---
layout: post
title: Annotation @Primary
permalink: /:collection/spring/annotation/primary
---

-	You might declare the @Component-annotated IceCream bean as the primary choice
-	Or, you can declare the IceCream bean explicitly in Java configuration (@Bean method )
-	You can configure your beans in XML, <bean> element has a primary attribute.
- When more than one bean is designated as primary, there are no primary candidates.


```java
@Autowired
public void setDessert(Dessert dessert) {
  this.dessert = dessert;
}
```
```java
@Component 
@Primary
public class Cake implements Dessert { ... }

@Component 
public class Cookies implements Dessert { ... }

@Component 
public class IceCream implements Dessert { ... }
```