---
layout: post
title: Bean Scopes
permalink: /:collection/spring/bean-scopes
---

Spring supports 5 scopes, 3 of which are available only if you use a web-aware ApplicationContext.  
***By default, all beans in Spring are singletons.***

```java
@Bean(scope = DefaultScopes.PROTOTYPE)
@Bean(scope = DefaultScopes.SESSION)
@ScopedProxy
```

|bean scopes||
|---|---|
|**singleton**|single instance per Spring IoC container (**default**).<br>To return the same bean instance each time one is needed|
|session|	Scopes a bean definition to an HTTP session. (web-aware ApplicationContext).|
|request|	Scopes a bean definition to an HTTP request. (web-aware ApplicationContext).|
|prototype|Scopes a single bean definition to have any number of object instances.<br>To force Spring to produce a new bean instance each time one is needed.|
|global-session|	Scopes a bean definition to a global HTTP session. (web-aware ApplicationContext).|

- Most of the time, singleton beans are ideal.
  - cost of instantiating and garbage collecting instances of objects that are only used for small tasks can’t be justified when an object is stateless and can be reused over and over again in an application.
- But sometimes you may find yourself working with a mutable class that does maintain some state and therefore isn’t safe for reuse.

**what is globalSession**
- globalSession is something which is connected to Portlet applications.
- When your application works in Portlet container it is built of some amount of portlets.
- Each portlet has its own session, but if your want to store variables global for all portlets in your application than you should store them in globalSession.
- This scope doesn't have any special effect different from session scope in Servlet based applications.

