---
layout: post
title: Logging
permalink: /:collection/spring/boot/logging
---

- Spring Boot comes with added support for Log4J2, Java Util Logging, and Logback.
    - Default - Logback
- It is usually pre-configured as console output.

```properties
#Logging
logging.level.org.springframework.web=DEBUG
logging.level.org.hibernate=ERROR
logging.config=logback.xml
```
```
spring.main.banner-mode=off
```
- **CONSOLE**: Print the banner to System.out.
- **LOG**: Print the banner to the log file.
- **OFF**: Disable printing of the banner.

# Logger (spring-boot-starter-logging)
```properties
logging.level=DEBUG, INFO
logging.file=Logbacklogging.log
logging.pattern.console= %d %-5level %logger %msg%n
logging.pattern.file= %d %-5level %logger %msg%n
```

# Logger (Log4j)
- spring-boot-starter-web
- exclusion-> spring-boot-starter-logging
- Add dependency spring-boot-starter-log4j2
- Create log4j2.xml

![logger]({{site.cdn}}/spring/spring-boot/logger.png)
