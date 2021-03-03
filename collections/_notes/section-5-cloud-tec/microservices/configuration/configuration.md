---
layout: post
title: Microservices Configuration
permalink: /:collection/microservices/configuration
---

- Separating code from configuration
  - properties
  - yaml
  - json
- Example Configurations
  - Database Connections
  - Credentials
  - Feature Flags
  - Business Logic Configuration parameters
  - Scenario Testing (A/B Testing)
  - SpringBoot Configuration
- Externalized - Externalize the property file
  - Add application.properties in the same folder as jar.
  - command line argument
- Environment Specific
- Consistent across all the instances
- Version History
- Real Time Management
- List all properties
  - Actuator - /configprops gives all properties

```
java -jar jarname-0.0.1-SNAPSHOT.jar --key="value"
```
For Local Server, user default value of properties
```java
@Value("${a:default}")
private String value;
```
