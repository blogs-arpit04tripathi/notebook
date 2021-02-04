---
layout: post
title: Wiring with the Spring Expression Language
permalink: /:collection/spring/wiring-with-spel
---

- TOC
{:toc}

<hr><br>

Spring Expression Language (SpEL), way of wiring values into a bean’s properties or constructor arguments using expressions that are evaluated at runtime.
-	The ability to reference beans by their IDs
-	Invoking methods and accessing properties on objects
-	Mathematical, relational, and logical operations on values
-	Regular expression matching
-	Collection manipulation

The first thing to know is that SpEL expressions are framed with #{ ... }, much as property placeholders are framed with ${ ... }. T() operator evaluates java.lang.System as a type to invoke staticcurrentTimeMillis().
```
#{sgtPeppers.artist}                  #{9.87E4}       #{false}
#{systemProperties['disc.title']}     #{'Hello'}      #{T(System).currentTimeMillis()}
```

```java
public BlankDisc(@Value("#{systemProperties['disc.title']}") String title, @Value("#{systemProperties['disc.artist']}") String artist) {
  this.title = title;
  this.artist = artist;
}
```
```xml
<bean id="sgtPeppers" class="soundsystem.BlankDisc"  
	c:_title="#{systemProperties['disc.title']}"
 	c:_artist="#{systemProperties['disc.artist']}" />
```

# Referencing beans, properties, and methods
```
#{sgtPeppers}       #{sgtPeppers.artist}        #{artistSelector.selectArtist()}
#{artistSelector.selectArtist().toUpperCase()}
#{artistSelector.selectArtist()?.toUpperCase()}
```
**?. Operator** - Makes sure the item to its left isn’t null before accessing the thing on its right. So, if selectArtist() returns null, then SpEL won’t even try to invoke toUpperCase(). The expression will evaluate to null.

# Working with types in expressions

-	The key to working with class-scoped methods and constants in SpEL is to use the T() operator. 
-	The result of the T() operator is a Class object that represents java.lang.Math. 
-	You can even wire it into a bean property of type Class, if you want. But the real value of the T() operator is that it gives you access to static methods and constants on the evaluated type.
```
#{T(java.lang.Math).PI * circle.radius ^ 2}         #{disc.title + ' by ' + disc.artist}
#{counter.total eq 100}                             #{counter.total == 100}
#{scoreboard.score > 1000 ? "Winner!" : "Loser"}
```

|Operator type|	Operators|
|---|---|
|Arithmetic|+, -, *, /, %, ^|
|Comparison| <, lt, >, gt, ==, eq, <=, le, >=, ge|
|Logical |and, or, not, \| |
|Conditional| ?: (ternary), ?: (Elvis)|
|Regular expression| matches|

Ternary operator - to check for a null value and offer a default value in place of the null. For example, the following expression evaluates to the value of disc.title if it isn’t null. If disc.title is null, then the expression evaluates to “Rattle and Hum”.
```
#{disc.title ?: 'Rattle and Hum'}
```

# Evaluating regular expressions

```xml
#{admin.email matches '[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\\.com'}
#{'This is a test'[3]} <!-- This references the fourth (zero-based) character in the String, or s. -->
```
SpEL also offers a selection operator (.?[]) to filter a collection into a subset of the collection. 
```
#{jukebox.songs.?[artist eq 'Aerosmith']}
```
SpEL also offers two other selection operations: 
-	.^[] for selecting the first matching entry
-	.$[] for selecting the last matching entry.

```
#{jukebox.songs.^[artist eq 'Aerosmith']}
#{jukebox.songs.![title]} - collection of all the song titles.
#{jukebox.songs.?[artist eq 'Aerosmith'].![title]}
```
SpEL offers a projection operator (.![]) to project properties from the elements in the collection onto a new collection.
