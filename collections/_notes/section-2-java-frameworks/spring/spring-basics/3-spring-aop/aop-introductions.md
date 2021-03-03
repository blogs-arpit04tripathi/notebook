---
layout: post
title: AOP Introductions
permalink: /:collection/spring/aop/introductions
---

- **Introduction** - aspects can attach new methods to Spring beans.
- Aspects are proxies that implement the same interfaces as the beans they wrap.
- Proxy can also be exposed through some new interface.
  - advised bean will appear to implement the new interface, even if its underlying implementation class doesn’t.
- When a method on the introduced interface is called,
  - proxy delegates the call to some other object that provides the implementation of the new interface.
  - Effectively, this gives you one bean whose implementation is split across multiple classes.

![]({{site.cdn}}/spring/spring-aop/aop-introduction.png)

```java
package concert;
public interface Encoreable {
 void performEncore();
}
```
```java
package concert;

import org.aspectj.lang.annotation.Aspect;
import org.aspectj.lang.annotation.DeclareParents;

@Aspect
public class EncoreableIntroducer {
  @DeclareParents(value="concert.Performance+", defaultImpl=DefaultEncoreable.class)
  public static Encoreable encoreable;
}
```
- Here, EncoreableIntroducer aspect doesn’t provide before, after, or around advice.
- **@DeclareParents** annotation is made up of three parts:
  - **value**
    - types of beans t be introduced with interface.
    - Here, anything that implements the Performance interface.
      - `+` sign at the end specifies any subtype of Performance, as opposed to Performance itself.
  -	**defaultImpl** - class providing default implementation.
  - **static property**
    - annotated by @DeclareParents
    - specifies interface to be introduced.
    - Here, Encoreable interface.

```xml
<bean class=”concert.EncoreableIntroducer” />
```

- When Spring discovers a bean annotated with @Aspect, it will automatically create a proxy.
- proxy delegates calls to either the target bean or interface implementation
  - depending on whether the method called belongs to the proxied bean or to the introduced interface.
