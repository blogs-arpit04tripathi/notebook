---
layout: post
title: Annotation - @Order
permalink: /:collection/spring/annotation/order
---

- `@Order` annotation defines the sorting order of an annotated component or bean.
- `Ordered.LOWEST_PRECEDENCE` is lowest (Default).
- `Ordered.HIGHEST_PRECEDENCE` is highest.

```
@Component
@Order(Ordered.LOWEST_PRECEDENCE)
```

For details, [click here](https://www.baeldung.com/spring-order){:target="_blank"}