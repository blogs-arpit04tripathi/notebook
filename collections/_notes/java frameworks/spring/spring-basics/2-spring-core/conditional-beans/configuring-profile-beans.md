---
layout: post
title: Configuring profile beans
permalink: /:collection/spring/configuring-profile-beans
---

- Environment-specific choices for Application, DB config, encryption algo, and integration with external systems.
  - rebuilt for each environment - configure each bean in a separate configuration class (or XML file) and make a build-time decision using profiles about which to compile into the deployable application.
  - Use Spring Profiles
- Rather than making that decision at build time, Spring waits to make the decision at runtime. 
- Consequently, the same deployment unit (perhaps a WAR file) will work in all environments without being rebuilt.
- You can use @Profile at the class and method level, alongside the @Bean annotation to specify the profile. 
- Any bean that isn’t given a profile will always be created, regardless of what profile is active.
- All the configuration XML files are collected into the deployment unit (likely a WAR file), but only those whose profile attribute matches the active profile will be used.


```java
@Configuration
public class DataSourceConfig {
 @Bean(destroyMethod="shutdown")
 @Profile("dev")
 public DataSource embeddedDataSource() {...}
}
```
