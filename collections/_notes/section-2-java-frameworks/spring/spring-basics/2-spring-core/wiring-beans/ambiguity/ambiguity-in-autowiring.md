---
layout: post
title: Ambiguity In Autowiring
permalink: /:collection/spring/ambiguity-in-autowiring
---

-	Autowiring only works when exactly one bean matches the desired result. 
-	When there’s more than one matching bean, the ambiguity prevents Spring from autowiring the property, constructor argument, or method parameter.
-	When spring doesn’t have a single, unambiguous choice, it throws **NoUniqueBeanDefinitionException**.

```java
@Autowired
public void setDessert(Dessert dessert) {
  this.dessert = dessert;
}
```
```java
nested exception is org.springframework.beans.factory.NoUniqueBeanDefinitionException:
No qualifying bean of type [com.desserteater.Dessert] is defined: expected single matching bean but found 3: cake,cookies,iceCream
```
```java
@Component 
public class Cake implements Dessert { ... }

@Component 
public class Cookies implements Dessert { ... }

@Component 
public class IceCream implements Dessert { ... }
```
-	You can declare one of the candidate beans as the primary choice.
-	You can use qualifiers to help Spring narrow its choices to a single candidate.

