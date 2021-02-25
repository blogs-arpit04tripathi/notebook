---
layout: post
title: Common Matchings
permalink: /:collection/java/regex/common-matchings
---

- TOC
{:toc}

<hr><br>

# Matching an Email Address

```java
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,5})$/
```
* **Group 1 ([a-z0-9_\.-]+)** 
	- In this section of the expression, we match one or more lowercase letters between a-z, numbers between 0-9, underscores, periods, and hyphens. The expression is then followed by an @ sign.
* **Group 2 ([\da-z\.-]+)**
	- Next, the domain name must be matched which can use one or more digits, letters between a-z, periods, and hyphens. The domain name is then followed by a period \..
* **Group 3 ([a-z\.]{2,5})**
	- Lastly, the third group matches the top level domain. This section looks for any group of letters or dots that are 2-5 characters long. This can also account for region-specific top-level domains.
* Therefore, with the regex expression above you can match many of the commonly used emails such as firstname.lastname@domain.com for example.

# Matching a Phone Number
```java
/^\b\d{3}[-.]?\d{3}[-.]?\d{4}\b$/
```
* **Section 1 \b\d{3}**
    - This section begins with a word boundary to tell regex to match the alpha-numeric characters. It then matches 3 of any digit between 0-9 followed by either a hyphen, a period, or nothing [-.]?.
* **Section 2 \d{3}**
    - The second section is quite similar to the first section, it matches 3 digits between 0-9 followed by another hyphen, period, or nothing [-.]?.
* **Section 3 \d{4}\b**
    - Lastly, this section is slightly different in that it matches 4 digits instead of three. The word boundary assertion is also used at the end of the expression. Finally, the end of the string is defined by the $.
* Therefore, with the above regex expression for finding phone numbers, it would identify a number in the format of 123-123-1234, 123.123.1234, or 1231231234.
