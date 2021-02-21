---
layout: post
title: String Methods
permalink: /:collection/java/strings/string-methods
---


|String Methods||
|---|---|
|String s = new String();                                               |
|String(char chars[ ])                                                  |
|**String(char chars[ ], int startIndex, int numChars)**                |char chars[]= {'a','b','c','d','e','f'}; `String s = new String(chars, 2, 3);` => cde
|String(StringBuffer buffer)                                            |
|String(StringBuilder builder)                                          |
|str.length()                                                           |"abc".length()
|str.charAt(int where)                                                  |"abc".charAt(1); => Returns b
|byte[ ] getBytes( )                                                    |`str.getBytes();`, `str.getBytes("UTF-16");`
|**char[ ] toCharArray( )**                                             |Entire String to char array
|**char[ ] getChars()**                                                 |str.getChars(srcStart, srcEnd, dest[], destStart);
|**boolean equals(Object str)**                                         |
|boolean equalsIgnoreCase(String str)                                   |
|**substring(int beginIndex, int endIndex)**                            |**beginIndex to endIndex–1**, endIndex is excluded.
|indexOf(String str, int startIndex)                                    |
|**indexOf(int ch, int startIndex)**                                    |first occurrence of a char or substring, **-1 on failure**
|**boolean startsWith(String str,int startIndx)**                       |"Foobar".startsWith("bar", 3)   => true
|**boolean startsWith(String str)**                                     |
|**boolean endsWith(String str)**                                       |
|lastIndexOf(int ch, int startIndex)                                    |
|**lastIndexOf(String str, int startIndex)**                            |
|**int compareTo(String str)**                                          | a.compareTo(str) => (a-str)
|int compareToIgnoreCase(String str)                                    |
|String substring(int startIndex)                                       |
|**String substring(int startIndx, int endIndx)**                       |
|**String concat(String str)**                                          |
|String replace(char original, char replacer)                           |
|**String replace(CharSequence o,CharSequence replacer)**               |
|**static String join(CharSequence delim, CharSequence . . . strs)**    |
|join(CharSequence delim, Iterable<? extends CharSequence> elements)    |
|intern()                                                               |
|**static String format(String format, Object... args)**                |String.format("My String is %.6f",12.121) --> 12.121000
|String **trim( )**                                                     |leading and trailing whitespace removed
|String **toLowerCase( )**                                              |
|String **toUpperCase( )**                                              |
|**int codePointAt(int i)**                                             |Unicode code point
|**boolean contains(CharSequence str)**                                 |
|**boolean isEmpty( )**                                                 |
|**boolean matches(String regex)**                                      | [PatternSyntaxException](https://docs.oracle.com/javase/7/docs/api/java/util/regex/PatternSyntaxException.html)|
|**CharSequence subsequence(int startIndex, int stopIndex)**            | 
|**String replaceFirst(regExp, newStr)**                                |
|**String replaceAll(regExp, newStr)**                                  |
|String[ ] split(String regExp)                                         |
|**String[ ] split(String regExp, int max)**                            |max - number of pieces <br> -ve value implies fully decomposed. <br> +ve, last entry contains remainder. <br> 0, fully decomposed, but no trailing empty strings included.|
