---
layout: post
title: Test Suites
permalink: /:collection/junit/test-suites
---

* Using **JUnit 5 test suites**, you can run tests spread into multiple test classes and different packages. 
* JUnit 5 provides two annotations to create test suites.
    - [@SelectPackages](http://junit.org/junit5/docs/current/api/index.html?org/junit/platform/runner/SelectPackages.html)
    - [@SelectClasses](http://junit.org/junit5/docs/current/api/index.html?org/junit/platform/runner/SelectClasses.html) 

* To execute the suite, you will use @RunWith(JUnitPlatform.class).
* Additionally, you can use following annotations for filtering test packages, classes or even test methods.
- @IncludePackages and @ExcludePackages to filter packages
- @IncludeClassNamePatterns and @ExcludeClassNamePatterns to filter test classes
- @IncludeTags and @ExcludeTags to filter test methods

```java
@RunWith(JUnitPlatform.class)
@SelectPackages("com.howtodoinjava.junit5.examples")
@IncludePackages("com.howtodoinjava.junit5.examples.packageC")
@ExcludeTags("PROD")
public class JUnit5TestSuiteExample{ }
```
