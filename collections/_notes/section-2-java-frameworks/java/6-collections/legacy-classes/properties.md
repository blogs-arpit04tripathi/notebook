---
layout: post
title: Properties
permalink: /:collection/java/collections/properties
---

* **Properties** is a subclass of **Hashtable**. 
* key and values are both **String**. 
* It is the type of object returned by **System.getProperties( )**.
* This variable holds a default property list associated with a Properties object. 
* **Constructors**: Properties( ) , Properties(Properties propDefault) - In both cases, the property list is empty.
* **Properties** also contains one deprecated method: **save( )** now replaced by **store( ) as save( )** did not handle errors correctly.

||
|---|
|String getProperty(String key)|
|String getProperty(String key, String defaultProperty)|
|void list(PrintStream streamOut)|
|void list(PrintWriter streamOut) |
|void load(InputStream streamIn) throws IOException|
|void load(Reader streamIn) throws IOException|
|void loadFromXML(InputStream streamIn) throws IOException, InvalidPropertiesFormatException|
|Enumeration<?> propertyNames( ) |
|Object setProperty(String key, String value) |
|void store(OutputStream streamOut, String description) throws IOException|
|void store(Writer streamOut, String description) throws IOException|
|void storeToXML(OutputStream streamOut, String description) throws IOException|
|void storeToXML(OutputStream streamOut, String description, String enc)|
|Set<String> stringPropertyNames( ) |

* When you construct a **Properties** object, you can pass another instance of Properties to be used as the default properties for the new instance. In this case, if you call **getProperty("foo")** on a given Properties object, and "foo" does not exist, Java looks for "foo" in the default Properties object. This allows for arbitrary nesting of levels of default properties.

# Using store( ) and load( )
One of the most useful aspects of Properties is that the information contained in a **Properties** object can be easily stored to or loaded from disk with the **store( )** and **load( )** methods. At any time, you can write a Properties object to a stream or read it back.

```java
Properties ht = new Properties();
FileInputStream fin = new FileInputStream("phonebook.dat");
ht.load(fin);
ht.put("name","myName");
FileOutputStream fout = new FileOutputStream("phonebook.dat");
ht.store(fout, "Telephone Book");
```
