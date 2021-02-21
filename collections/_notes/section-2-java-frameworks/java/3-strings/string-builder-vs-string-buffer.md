---
layout: post
title: StringBuilder and StringBuffer
permalink: /:collection/java/strings/string-builder-and-string-buffer
---

# StringBuffer
* StringBuffer - growable and modifiable character sequence. 
* **Default, extra 16 additional characters** as reallocation is costly and frequent reallocations can fragment memory.
* StringBuffer method are synchronized hence thread-safe.

# StringBuilder
- Non Thread safe version.

# StringBuffer vs StringBuilder

|                       |StringBuffer  |StringBuilder |
|---                    |---           |---           |
|**synchronization**    |Yes           |No
|**thread-safety**      |Yes           |No
|**speed**              |Slow          |Fast

# Why 3 classes - String, StringBuilder, StringBuffer

***Why do one need three classes for same functionality, why can't String just do what StringBuilder and StringBuffer does?***  
- For keeping String mutable, due to many reasons like Security, String Pool, and Performance.
- So, Java API designers introduced a pattern of providing mutable companion class for immutable main class.
