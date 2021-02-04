---
layout: post
title: Spring Bean Definition Metadata
permalink: /:collection/spring/bean-metadata
---

Bean definition contains the information called configuration metadata, which is needed for the container to know the following −
- How to create a bean
- Bean's lifecycle details
- Bean's dependencies

```java
@Bean("accountService")
@Scope(value = ConfigurableBeanFactory.SCOPE_PROTOTYPE)
@Scope(value=WebApplicationContext.SCOPE_SESSION, proxyMode=ScopedProxyMode.INTERFACES)
```

|||
|---|---|
|class|	Mandatory attribute to specify the bean class used to create the bean.|
|name|	Specifies bean identifier uniquely. In XMLbased configuration metadata, you use the id and/or name attributes to specify the bean identifier(s).|
|scope|	Specifies the scope of the objects created from a particular bean definition.|
|constructor-arg|	This is used to inject the dependencies.|
|properties|	This is used to inject the dependencies.|
|autowiring mode|	This is used to inject the dependencies.|
|lazy-initialization mode |	A lazy-initialized bean tells the IoC container to create a bean instance when it is first requested, rather than at the startup.|
|initialization method|	A callback just after all necessary properties of bean have been set by container.|
|destruction method|	A callback to be used when the container containing the bean is destroyed.|

Following are the three important methods to provide configuration metadata to the Spring Container
- XML based configuration file.
- Annotation-based configuration
- Java-based configuration

