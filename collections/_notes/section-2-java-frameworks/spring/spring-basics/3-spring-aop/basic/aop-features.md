---
layout: post
title: Spring AOP features
permalink: /:collection/spring/aop/aop-features
---

- Spring ***advises objects at runtime***.
- aspects are woven into Spring-managed beans at runtime ***by wrapping them with a proxy class***.
- proxy class poses as the target bean, intercepting advised method calls and forwarding those calls to the target bean. 
  - `intercept method call --> performs the aspect logic --> invokes target bean’s method`
- ***Lazy Loading*** - Spring doesn’t create a proxied object until that proxied bean is needed by the application.
- For ApplicationContext, proxied objects created when it loads all the beans from the BeanFactory.
- As Spring creates proxies at runtime, ***you don’t need a special compiler to weave aspects in Spring’s AOP***.

**Spring only supports method join points**
- Only method pointcuts.
- No field pointcuts, can't apply advice when field is updated.
- No constructor pointcuts, can't apply advice when a bean is instantiated. 
- If you need field or constructor pointcuts, use AspectJ with Spring AOP.

**What do you mean by Proxy in Spring Framework?**  
- **Proxy** - object created after applying advice to a target object.
- In case of client objects the target object and the proxy object are the same.

**In Spring, what is Weaving?** 
- The process of creating advised object (proxy) by applying advice is called **Weaving**.
- In Spring AOP, ***weaving is performed at runtime***.

![]({{site.cdn}}/spring/spring-aop/aop-proxy.png)
