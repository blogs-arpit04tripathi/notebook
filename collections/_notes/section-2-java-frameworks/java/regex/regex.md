---
layout: post
title: RegEx (Regular Expression)
permalink: /:collection/java/regex/
---

* ***Pattern of regex is applied on String from left to right and source char in a match can’t be reused.***
* For example, regex “121” will match “31212142121” only twice as “_121____121”.

```java
System.out.println("Using String matches method: " + str.matches(".bb"));
System.out.println("Using Pattern matches method: " + Pattern.matches(".bb", str));
Pattern.matches(“[a - e1 - 3].”, “d#”)
```
```java
import java.util.regex package;

public class PatternExample {
    public static void main(String[] args) {
        try {
            Pattern pattern = Pattern.compile(".xx.");
            Matcher matcher = pattern.matcher("MxxY");
            System.out.println("Input String matches regex - " + matcher.matches());
            pattern = Pattern.compile("*xx*"); // bad regular expression
        } catch (PatternSyntaxException pse) {
            System.out.println(e.getMessage());
        }
    }
}
```

# Capturing Groups

* () in regex is used to treat multiple characters as a single unit.
* portion of input matching the capturing group is saved into memory and can be recalled using **Backreference**.
* **matcher.groupCount()** method - find number of capturing groups.
* For example, ((a)(bc)) contains 3 capturing groups – ((a)(bc)), (a) and (bc).
* You can use **Backreference** in regular expression with backslash (\) and then the number of groups to be recalled.

```java
System.out.println(Pattern.matches("(\\w\\d)\\1", "a2a2"));         	//true  \1 is a2
System.out.println(Pattern.matches("(\\w\\d)\\1", "a2b2"));         	//false \1 is a2
System.out.println(Pattern.matches("(AB)(B\\d)\\2\\1", "ABB2B2AB"));	//true  \1 is AB
System.out.println(Pattern.matches("(AB)(B\\d)\\2\\1", "ABB2B3AB"));	//false \2 is B2
```
