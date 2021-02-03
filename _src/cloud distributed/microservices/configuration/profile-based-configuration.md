---
layout: post
title: Profile Based Config
permalink: /microservices/configuration/profile-based
---

you can also select beans based on active profile.
- `application-<profile-name>.properties`
- `application-<profile-name>.yaml`
- **default profile is always active.**

```
java -jar jar-name.jar --spring.profiles.active=dev
```
```java
@Autowired
Environment env;

env.getXXX();
```

![](https://github.com/arpit04tripathi/files-cdn/raw/cdn/webservices/microservices/config-env-specific.png)
