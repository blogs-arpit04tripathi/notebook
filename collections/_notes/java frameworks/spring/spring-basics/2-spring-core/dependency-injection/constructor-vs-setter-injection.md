---
layout: post
title: Constructor vs Setter Injection
permalink: /:collection/spring/constructor-vs-setter-injection
---

|Constructor Injection                                      |	Setter Injection|
|---                                                        |---|	
|There is no partial injection.                             |	partial dependency can be injected|
|doesn’t override the setter property.                   |	overrides the constructor property.|
|It will create a new instance if any modification is done. |	It will not create new instance if any modification is done.|
|It works better for many properties.                       |	It works better for few properties.|

**When will you use “Constructor Injection” and “Setter Injection”?**
- **Constructor Injection**
  - allows you to hide immutable fields from users of your class.
  - Immutable classes don’t declare setter methods.
    - This also enforces that you have the valid objects at the construction time.
    - It also prompts you to rethink about your design when you have too many constructor parameters.
- **Setter Injection**
  - constructors may get a lot of parameters
    - hence needing a lot of overloaded constructors for all possible ways of object creation.