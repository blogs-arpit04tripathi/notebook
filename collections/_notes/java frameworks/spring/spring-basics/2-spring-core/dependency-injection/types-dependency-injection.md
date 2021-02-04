---
layout: post
title: Types Of Dependency Injection
permalink: /:collection/spring/types-dependency-injection
---

- constructor injection - for hard dependencies
- field injection - any optional dependencies.

|Dependency Injection||
|---|---|
|Constructor Injection|	Dependencies are provided as **constructor parameters**.|
|Setter Injection     |	Dependencies are assigned through **setter methods**.   |
|Field injection      |	Using annotations on fields and parameters.             |
|Interface Injection  | Clients implements interface that exposes a setter method that accepts the dependency.      |

```java
// Interface Injection
public interface EngineMountable {
    void mount(Engine engine);
}

public class Car implements EngineMountable {
    private Engine engine;
    
    //dependency injection
    @Override
    public void mount(Engine engine){
        this.engine = engine;
    }
}
```