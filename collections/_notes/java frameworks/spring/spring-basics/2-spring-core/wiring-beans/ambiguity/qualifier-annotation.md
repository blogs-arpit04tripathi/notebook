---
layout: post
title: Annotation @Qualifier
permalink: /:collection/spring/annotation/qualifier
---

- Limitation of @Primary - doesn’t limit choices to a single unambiguous option, it only designates a preferred option.
- @Qualifier - can be used with @Autowired or @Inject to specify which bean you want to be injected. 
- @Qualifier parameter is the ID of the bean that you want to inject.

```java
@Autowired
@Qualifier("iceCream")
public void setDessert(Dessert dessert) {this.dessert = dessert;}
```
- Due to harcoded bean id in @Qualifier, basing qualification on the default bean ID qualifier is simple but can pose some problems.
- What do you suppose would happen if you refactored the IceCream class, renaming it Gelato? Autowiring would fail.

# Custom Qualifiers

```java
@Component
@Qualifier("cold")
public class IceCream implements Dessert {..}

@Bean
@Qualifier("cold")
public Dessert iceCream() {
    return new IceCream();
}
```
```java
@Autowired
@Qualifier("cold")
public void setDessert(Dessert dessert) {
    this.dessert = dessert;
}
```

- Instead of relying on the bean ID as the qualifier, you can assign your own qualifier to a bean.
- When defining custom @Qualifier values, it’s a good practice to use a trait or descriptive term for the bean, rather than using an arbitrary name.
- In this case, I’ve described the IceCream bean as a “cold” bean.
- At the injection point, it reads as “give me the cold dessert,” which happens to describe IceCream.
- Similarly, I might describe Cake as “soft” and Cookies as “crispy.”
