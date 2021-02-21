---
layout: post
title: Modifying a String
permalink: /:collection/java/strings/modification
---


* String are immutable, copy it to **StringBuffer** or **StringBuilder** and create string after modifications.
* All these methods new String which needs to assigned back if updated one is required in code.

# toLowerCase()
* **Internally calls toLowerCase(Locale.getDefault())**.
* locale sensitive (**internationalization (i18n)**).
* **Do not write a logic around it interpreting locale independently**.

```java
BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
String str = br.readLine();    
str = str.trim();
```
```java
List<String> list = Arrays.asList("Steve", "Rick", "Peter", "Abbey");
String names = String.join(" | ", list);            
Output - Steve | Rick | Peter | Abbey
```
```java
//Java automatically interns this
String str1 = "beginnersbook";
// intern() method searches "beginnersbook" in the memory pool and returns the reference of it.
String str2 = new String("beginnersbook").intern(); 
System.out.println("str1==str2: "+(str1 == str2));     //prints true 
```

# Changing the Case of Characters Within a String
* Your application selects default locale.
* **toLowerCase() is locale specific**.
* Code logic based on string length is a nice catch in code review.
* You can use toLowerCase(Locale.English) but here you lose internationalization.

```java
import java.util.Locale; 
Locale.setDefault(new Locale("lt"));        //Lithuanian
String str = "\u00cc";                      // Ì
String lowerCaseStr = str.toLowerCase();    // iı`
// length was 1, after toLowerCase length is 3
```

# split(String regExp, int max)
* max - number of pieces
  * -ve value implies fully decomposed.
* +ve, last entry contains remainder. 
* 0, fully decomposed, but no trailing empty strings included.
