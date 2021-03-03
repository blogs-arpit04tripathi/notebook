---
layout: post
title: ApplicationContext
permalink: /:collection/spring/core/ioc-container/application-context
---

**Why Prefer ApplicationContext over BeanFactory?**  
- Application contexts are preferred over bean factories.
- BeanFactory can still be used for lightweight applications like mobile devices or applet-based applications where data volume and speed is significant.

```java
Interface ApplicationContext 
extends ListableBeanFactory, HierarchicalBeanFactory, MessageSource, ApplicationEventPublisher, ResourcePatternResolver.
```

An ApplicationContext provides:
-	Bean factory methods for accessing application components, inherited from ListableBeanFactory.
-	The ability to resolve messages (internationalization), Inherited from the MessageSource  interface.
-	The ability to publish events to registered listeners. Inherited from the ApplicationEventPublisher interface.
-	The ability to load file resources in a generic fashion. Inherited from the ResourceLoader interface.
-	Inheritance from a parent context.
    -	Definitions in a descendant context will always take priority.
    -	A single parent context can be used by an entire web application, while each servlet has its own child context that is independent of that of any other servlet.

Apart from standard BeanFactory lifecycle capabilities, ApplicationContext implementations detect and invoke ApplicationContextAware beans as well as ResourceLoaderAware, ApplicationEventPublisherAware and MessageSourceAware beans.

