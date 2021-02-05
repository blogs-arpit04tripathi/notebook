---
layout: post
title: Conditional Execution
permalink: /:collection/junit/conditional-execution
---

```java
@EnabledOnOS(OS.LINUX)
@EnabledOnJre(JRE.JAVA_11)
@EnabledIf
@EnabledIfSystemProperty
@EnabledIfEnvironmentVariable
```

Other way for conditional execution is to use assumptions.
