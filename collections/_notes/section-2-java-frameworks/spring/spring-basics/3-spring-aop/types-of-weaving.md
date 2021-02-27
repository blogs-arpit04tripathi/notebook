---
layout: post
title: Types of Weaving
permalink: /:collection/spring/aop/types-of-weaving
---

The **weaving** can take place at several points in the target object’s lifetime:

|Weaving Types||
|---|---|
|**Compile time** | Aspects are woven in when the target class is compiled. <br>This requires a special compiler. <br>AspectJ’s weaving compiler weaves aspects this way.|
|**Class load time** | Aspects are woven in when the target class is loaded into the JVM. <br>This requires a special ClassLoader that enhances the target class’s bytecode before the class is introduced into the application. <br>AspectJ 5’s load-time weaving (LTW) support weaves aspects this way.|
|**Runtime** | Aspects are woven in sometime during the execution of the application. <br>Typically, an AOP container dynamically generates a proxy object that delegates to the target object while weaving in the aspects. <br>This is how Spring AOP aspects are woven. <br>Slowest of all.|

![]({{site.cdn}}/spring/spring-aop/aop-implementation.png)
