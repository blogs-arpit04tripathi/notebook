---
layout: post
title: Strings FAQ
permalink: /:collection/java/strings/faq
---

- TOC
{:toc}

<hr><br>

# Why character array is better than String for Storing password in Java?
* **Strings are immutable in Java**, password as plain text will remain in memory until Garbage collection cycle.
* Can be accessed via String pool (remain in memory for long duration), this poses a security threat.
* any one with access to memory dump can find the password, always use encrypted password.
* for char[], can set all elements as blank or zero. **character array mitigates security risk of stealing password.**
* **Java itself recommends** using getPassword() of JPasswordField returning char[] and deprecated getText().
* risk of printing plain text in log file or console, for Array its memory location get printed.
* using char[] is not enough, need to erase content to be more secure.
* Use hash'd or encrypted password and clear it from memory as soon as authentication is completed.

```java
String strPassword="Unknown";                               //String password: Unknown
char[] charPassword= new char[]{'U','n','k','w','o','n'};   //Character password: [C@110b053
```

# Ways to check if String is empty in Java?

|Check empty string        ||
|---                       |---
**string.length()**        |if(string != null && string.length() == 0){ return true; }
**equals()**               |"".equals(input);
**isEmpty()**              |if(string != null && string.isEmpty()){ return true; }
**StringUtils**            |StringUtils.isEmpty("")    // apache lang3
**StringUtils.hasLength()**|StringUtils.hasLength(null) = false

# Reverse a string

```java
String reverse = new StringBuffer(word).reverse().toString();
reverse = new StringBuilder(word).reverse().toString();
```

# Ways to Concatenate?
* Concatenation operator (+)
* StringBuffer append()
* StringBuilder append()
* String.concat()

![concat.png]({{site.cdn}}/java/strings/concat.png)
