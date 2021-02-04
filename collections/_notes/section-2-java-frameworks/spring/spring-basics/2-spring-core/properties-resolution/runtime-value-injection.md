---
layout: post
title: Runtime value injection
permalink: /:collection/spring/runtime-value-injection
---

- Spring offers two ways of evaluating values at runtime:
  -	Property placeholders
  -	The Spring Expression Language (SpEL)

# Injecting external values
The simplest way to resolve external values in Spring is to declare a property source and retrieve the properties via the Spring Environment.

```properties
# /resource/app.properties
disc.title=Sgt. Peppers Lonely 
disc.artist=The Beatles
```
```java
@Configuration
@PropertySource("classpath:/resource/app.properties")
public class ExpressiveConfig {
  @Autowired
  Environment env;

  @Bean
  public BlankDisc disc() {
    return new BlankDisc(env.getProperty("disc.title"), env.getProperty("disc.artist"));
  }
}
```
- This properties file is loaded into Spring’s Environment, from which it can be retrieved later.
- Meanwhile, in the disc() method, a new BlankDisc is created; its constructor arguments are resolved from the properties file by calling getProperty().
-	If either the disc.title property or the disc.artist property is undefined, an **IllegalStateException** will be thrown.

```java
int connectionCount = env.getProperty("db.connection.count", Integer.class, 30);
boolean titleExists = env.containsProperty("disc.title");
Class<CompactDisc> cdClass = env.getPropertyAsClass("disc.class", CompactDisc.class);
```
-	If you want to check for the existence of a property, you can call containsProperty() on Environment.
-	If you need to resolve a property into a Class, you can use the getPropertyAsClass() method.
-	Spring also offers the option of wiring properties with placeholder values that are resolved from a property source.

# Methods offered by Environment
```java
String getProperty(String key)                            // overloaded 4 ways
String getProperty(String key, String defaultValue)
T getProperty(String key, Class<T> type)
T getProperty(String key, Class<T> type, T defaultValue)

// Environment also offers some methods for checking which profiles are active
String[] getActiveProfiles()                  // Returns an array of active profile names
String[] getDefaultProfiles()                 // Returns an array of default profile names
boolean acceptsProfiles(String... profiles)   // Returns true if the environment supports the given profile(s)
```
