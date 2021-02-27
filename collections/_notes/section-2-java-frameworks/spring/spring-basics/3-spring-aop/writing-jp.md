---
layout: post
title: Writing pointcuts
permalink: /:collection/spring/aop/writing-jp
---

![]({{site.cdn}}/spring/spring-aop/joinPoint.png)

```java
package concert;
public interface Performance {
    public void perform();
}
```
- within() - confine pointcut to only specific packager.

```java
execution(* concert.Performance.perform()) and bean('woodstock')
execution(* concert.Performance.perform()) and !bean('woodstock')
```
```
"||" or "or" - OR relationship
"!" or "not" – negate
```
