---
layout: post
title: StringBuffer Methods
permalink: /:collection/java/strings/string-buffer-methods
---


|StringBuffer Methods                                                         |     |
|---                                                                          |---  |
|**StringBuffer(int size)**                                                   |
|**int capacity( )**                                                          | total allocated capacity
|**void ensureCapacity(int minCapacity)**                                     |minCapacity - min size of the buffer (larger may be allocated for efficiency.)
|**StringBuffer(String str)**                                                 |
|**int length( )**                                                            | current length
|**setLength(int len)**                                                       |len > str.length(), null characters added to the end else characters are lost.
|StringBuffer(CharSequence chsq)                                              |
|**char charAt(int where)**                                                   |
|**void setCharAt(int where, char ch)**                                       |
|**StringBuffer deleteCharAt(int loc)**                                       |
|**StringBuffer append(String str)**                                          |
|StringBuffer append(Object obj)                                              |
|**reverse( )**                                                               |
|**StringBuffer delete(startIndex, endIndex)**                                |
|**StringBuffer insert(int index, String str)**                               |
|**getChars(int sourceStart, int sourceEnd, char target[ ], int targetStart)**|
|**StringBuffer replace(startIndex, endIndex, String str)**                   |
|String substring(int startIndex)                                             |
|**String substring(startIndex, endIndex)**                                   |
|int indexOf(String str)                                                      |
|**int indexOf(String str, int startIndex)**                                  |
|int lastIndexOf(String str)                                                  |
|**int lastIndexOf(String str, int startIndex)**                              |
|**void trimToSize( )**                                                       | size reduced to better fit the current contents.
