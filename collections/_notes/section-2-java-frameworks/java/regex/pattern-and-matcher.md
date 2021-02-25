---
layout: post
title: Pattern and Matcher
permalink: /:collection/java/regex/pattern-and-matcher
---

* Pattern object with flags, Pattern.CASE_INSENSITIVE enables case insensitive matching.
* Pattern class also provides split(String) method that is similar to String class split() method.
* Pattern class toString() - regex String from which pattern was compiled.
* Matcher classes have start() and end() index methods that show precisely where the match was found in the input string.
* Matcher class provides - replaceAll(String replacement) and replaceFirst(String replacement).

```java
package com.journaldev.util;
import java.util.regex.Matcher;
import java.util.regex.Pattern;
public class RegexExamples {
    public static void main(String[] args) {
        // using pattern with flags
        Pattern pattern = Pattern.compile("ab", Pattern.CASE_INSENSITIVE);
        Matcher matcher = pattern.matcher("ABcabdAb");
        // using Matcher find(), group(), start() and end() methods
        while (matcher.find()) {
            System.out.println("Found the text \"" + matcher.group() +
                "\" starting at " + matcher.start() +
                " index and ending at index " + matcher.end());
        }
        // using Pattern split() method
        pattern = Pattern.compile("\\W");
        String[] words = pattern.split("one@two#three:four$five");
        for (String s: words) {
            System.out.println("Split using Pattern.split(): " + s);
        }
        // using Matcher.replaceFirst() and replaceAll() methods
        pattern = Pattern.compile("1*2");
        matcher = pattern.matcher("11234512678");
        System.out.println("Using replaceAll: " + matcher.replaceAll("_"));
        System.out.println("Using replaceFirst: " + matcher.replaceFirst("_"));
    }
}
```
```java
Output of the above java regex example program is.
Found the text "AB" starting at 0 index and ending at index 2
Found the text "ab" starting at 3 index and ending at index 5
Found the text "Ab" starting at 6 index and ending at index 8
Split using Pattern.split(): one
Split using Pattern.split(): two
Split using Pattern.split(): three
Split using Pattern.split(): four
Split using Pattern.split(): five
Using replaceAll: _345_678
Using replaceFirst: _34512678
```