---
layout: post
title: Rules of overriding (restricting is allowed)
permalink: /:collection/java/rules-for-overriding
---

- **Access Modifier**
  * can increase accessibility, but cannot reduce.
  * **can not** reduce accessibility. `public ==> protected [x]`
  * **can** increase accessibility.   `protected ==> protected or public`
- **Exception - Checked Exception**
  * can change to throw subtype of checked exception but not the supertype.
  * **can not** throw checked Exception which is higher in hierarchy. `IOException ==> java.lang.Exception [x]`
    * Above rule **doesn't apply to RuntimeException** as it’s not needed to be declared in throws clause.
  * **change the number of exceptions** - Yes, exceptions must be compatible with throws clause of super
- **Exception - Unchecked Exception**
  * **unchecked to checked** – **No** `[x]`
  * **checked to unchecked** – Yes, reverse is not possible. 
    * SQLException to NumberFormatException - Yes
  * **Without throws clause to with throws** – Yes, Unchecked only.
