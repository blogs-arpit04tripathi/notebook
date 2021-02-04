---
layout: post
title: Automatic Wiring
permalink: /:collection/spring/automatic-wiring
---

***Why bother explicitly wiring beans together if Spring can be configured to automatically do it for you?***
- Spring attacks automatic wiring from two angles:
  - **Component scanning** - Spring automatically discovers beans to be created in the application context.
  - **Autowiring** - Spring automatically satisfies bean dependencies.

**Creating Discoverable Beans**
- **@Component** - identifies as a component class and serves as a clue to Spring that a bean should be created for the class.
- Component scanning isn’t turned on by default.
  - You’ll still need to write an explicit configuration to tell spring to seek out classes annotated with @Component and to create beans from them. 
- With no further configuration, **@ComponentScan** will default to scanning the same package as the configuration class.

```java
// ComponentScan
@Configuration
@ComponentScan(basePackages= {"soundsystem", "video"})
public class CDPlayerConfig {}

@Configuration
@ComponentScan(basePackageClasses={CDPlayer.class, DVDPlayer.class})
public class CDPlayerConfig {}
```

**Naming a Component-Scanned Bean**
- All beans in a Spring application context are given an ID, derived from its class name by lowercasing the first letter of the class name.
- Spring supports the @Named annotation as an alternative to @Component.

```java
@Component("lonelyHeartsClub")
public class SgtPeppers implements CompactDisc {}

import javax.inject.Named;
@Named
public class CDPlayer {}
```

**Setting Base Package for component Scanning**
- For setting the base packages, values are expressed as String which is not very type-safe.
- If you were to refactor the packagenames, the specified base packages would be wrong.

**Annotating beans to be automatically wired**
- ***Autowiring*** - Letting Spring automatically satisfy a bean’s dependencies by finding other beans in the application context that are a match to the bean’s needs.
- `@Autowired` or `@Inject` indicates that autowiring should be performed.
- @Autowired can also be applied on any method on the class.
- Assuming that one and only one bean matches, that bean will be wired in.
  - If there are no matching beans, Spring will throw an exception as the application context is being created. 
  -	To avoid that exception, you can set the required attribute on @Autowired to false. 
    - Leaving the property unwired could lead to NullPointerExceptions if you don’t check for null in your code.
- In the event that multiple beans can satisfy the dependency, Spring will throw an exception indicating ambiguity in selecting a bean for autowiring.

```java
// Constructor Injection
@Autowired(required=false)
public CDPlayer(CompactDisc cd){ this.cd = cd;}

import javax.inject.Inject;
@Inject
public CDPlayer(CompactDisc cd){  this.cd = cd;}
```