---
layout: post
title: Best Practices for Exception Handling
permalink: /:collection/java/exceptions/best-practices
---


|Exception Handling Best Practices|   |
|---|---|
|Use Specific Exceptions|Even JDK has specific Exception: IOException with further sub-classes as FileNotFoundException, EOFException etc.<br>so that caller will easily know the root cause, this makes debugging easy.|
|Throw Early or Fail-Fast|throw exceptions as early as possible to make stack trace shorter and readable.|
|Catch Late|catch exception only if we can handle it appropriately otherwise throw exceptions back to the caller to handle it.|
|Closing Resources|close all resources in finally block or use try-with-resources.|
|Logging Exceptions|always log exception messages and give clear message when throwing.<br>[x] Avoid empty catch blocks|
|Single catch block for multiple exceptions|single catch block reduces code size.|
|Using Custom Exceptions|create a custom exception with error code and caller program can handle these error codes.<br>Its also a good idea to create a utility method to process different error codes and use it.|
|Naming Conventions and Packaging|class name ends with Exception.|
|Use Exceptions Judiciously|Many times it is required to see if some operation worked, return Boolean in that case.|
|Document the Exceptions Thrown|Use javadoc @throws, useful when providing as interface to other applications.|
