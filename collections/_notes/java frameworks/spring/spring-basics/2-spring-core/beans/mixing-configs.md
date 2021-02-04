---
layout: post
title: Importing and mixing configurations
permalink: /:collection/spring/mixing-configs
---

- TOC
{:toc}

<hr><br>

Autowiring considers all beans in the Spring container, regardless they were declared in JavaConfig or XML or picked up by component scanning.

```java
@Configuration
public class CDConfig {
    @Bean
    public CompactDisc compactDisc() { return new SgtPeppers(); }
}
```
```java
@Configuration
@Import(CDConfig.class)
public class CDPlayerConfig {
    @Bean
    public CDPlayer cdPlayer(CompactDisc compactDisc) {
            return new CDPlayer(compactDisc);
    }
}
```
You can leave @Import out of CDPlayerConfig and instead create a higher-level SoundSystemConfig that uses @Import to bring both configurations together.
```java
@Configuration
@Import({CDPlayerConfig.class, CDConfig.class})
public class SoundSystemConfig {}
// 2nd level - (java + java config import)
```
```java
@Configuration
@Import(CDPlayerConfig.class)
@ImportResource("classpath:cd-config.xml")
 public class SoundSystemConfig {} 
// 2nd level - (java + xml config import)
```

# Referencing JavaConfig in XML configuration
```xml
<import resource="cd-config.xml" />
<bean id="cdPlayer" class="soundsystem.CDPlayer" c:cd-ref="compactDisc" />
```
The \<import> element only works to import other XML configuration files, and there isn’t an XML element whose job it is to import JavaConfig classes. There is, however, an element you already know that can be used to bring a Java configuration into an XML configuration: the \<bean> element.
```xml
<bean class="soundsystem.CDConfig" />
<bean id="cdPlayer" class="soundsystem.CDPlayer" c:cd-ref="compactDisc" />

<bean class="soundsystem.CDConfig" />
<import resource="cdplayer-config.xml" />
```
Whether using JavaConfig or XML wiring, often create a root configuration, as I’ve shown here, that brings together two or more wiring classes and/or XML files. It’s in this root configuration that I’ll also usually turn on component scanning (with either \<context:component-scan> or @ComponentScan).
