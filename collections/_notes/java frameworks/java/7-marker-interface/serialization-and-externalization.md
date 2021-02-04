---
layout: post
title: Serialization and Externalization
permalink: /java/marker-interface/serialization-and-externalization
---

- TOC
{:toc}

<hr><br>

# Serialization

![serialization-deserialization](https://github.com/arpit04tripathi/files-cdn/raw/cdn/java/marker-interface/serialization-deserialization.png)

* to convert Object into a binary format which can be persisted into disk or sent over network.
* Java Serialization API - `java.io.Serializable`, `java.io.Externalizable`, `ObjectInputStream` and `ObjectOutputStream`.

### How to make a class serializable?
* implement java.io.Serializable interface and JVM will take care of serializing object in default format.
* it can potentially limit your to further modify and change its implementation as it can potentially break default serialization.
* If you don't explicitly declare ***SerialVersionUID*** then JVM generates its based upon structure of class which depends upon interfaces a class implements and several other factors which is subject to change. object serialized by old version of your program you will get **InvalidClassException**.

### Difference between Serializable and Externalizable interface
- Externalizable provides us ***writeExternal()*** and ***readExternal()*** method which gives us flexibility to control java serialization mechanism instead of relying on Java's default serialization.

### What is serialVersionUID? What would happen if you don't define this?
* an ID which is stamped on object when it get serialized usually hashcode of object.
* you can use tool serialver to see serialVersionUID of a serialized object.
* SerialVersionUID is used for version control of object. you can specify serialVersionUID in your [class file](https://javarevisited.blogspot.com/2012/05/10-points-about-class-file-in-java.html){:target="_blank"} also.
* If not specified, then already serialized class will not be able to recover as new serialVersionUID generated for the class.
* Java serialization process relies on correct serialVersionUID for recovering state of serialized object and throws **java.io.InvalidClassException in case of serialVersionUID mismatch**.

### While serializing you want some of the members not to serialize? How do you achieve it?
- If you don't want any field to be part of object's state then declare it either ***static or transient*** based on your need and it will not be included during Java serialization process.

### What will happen if one of the members in the class doesn't implement Serializable interface?
- If you try to serialize an object of a class which implements Serializable, but the object includes a reference to an non-Serializable class then a **NotSerializableException** will be thrown at runtime.
- Always put a **SerializableAlert** (comment section in my code) , one of the [code comment best practices](https://javarevisited.blogspot.com/2011/08/code-comments-java-best-practices.html), to instruct developer to remember this fact while adding a new field in a Serializable class.

### If a class is Serializable but its super class in not, what will be the state of the instance variables inherited from super class after deserialization?
- Values of the ***instance variables inherited from super class will be initialized by calling constructor of Non-Serializable Super class during deserialization process***. Once the [constructor chaining](https://javarevisited.blogspot.com/2012/01/what-is-constructor-overloading-in-java.html) will started it wouldn't be possible to stop that, hence even if classes higher in hierarchy implements Serializable interface, there constructor will be executed.

### Can you Customize Serialization process or can you override default Serialization process in Java?
* Serializing - `ObjectOutputStream.writeObject(saveThisobject)` is invoked.
* Reading - `ObjectInputStream.readObject()` is invoked.
* If you define these two methods in your class then JVM will invoke these two methods instead of applying default serialization mechanism. 
* You can customize behavior of object serialization and deserialization here by doing any kind of pre or post processing task.
* Important point to note is ***making these methods private to avoid being inherited***, [overridden or overloaded](https://javarevisited.blogspot.com/2011/12/method-overloading-vs-method-overriding.html). Since only Java Virtual Machine can call private method integrity of your class will remain and Java Serialization will work as normal.

### Why is custom serialization needed?
* **transient** keyword is used on the variables which we don’t want to serialize and is data loss to some extent. 
* But sometimes, it is needed to serialize them in a different manner than the default serialization (such as encrypting before serializing etc.), in that case, we have to use custom serialization and deserialization.

```java
// Java program to illustrate customized serialization 
import java.io.*;
class GfgAccount implements Serializable {
    String username = "gfg_admin";
    transient String pwd = "geeks";
    // Performing customized serialization using the below two methods: 
    // this method is executed by jvm when writeObject() on Account object reference in main method is executed by jvm. 
    private void writeObject(ObjectOutputStream oos) throws Exception {
        oos.defaultWriteObject();   // to perform default serialization of Account object.
        String epwd = "123" + pwd;  // epwd (encrypted password)
        oos.writeObject(epwd);      // writing encrypted password to the file 
    }

    // this method is executed by jvm when readObject() on Account object reference in main method is executed by jvm. 
    private void readObject(ObjectInputStream ois) throws Exception {
        ois.defaultReadObject();                    // performing default deserialization of Account object
        String epwd = (String) ois.readObject();    // deserializing the encrypted password from the file
        pwd = epwd.substring(3);                    // decrypting it and saving it to the original password
    }
}

class CustomizedSerializationDemo {
    public static void main(String[] args) throws Exception {
        GfgAccount gfg_g1 = new GfgAccount();
        System.out.println("Username :" + gfg_g1.username + " Password :" + gfg_g1.pwd);
        FileOutputStream fos = new FileOutputStream("abc.ser");
        ObjectOutputStream oos = new ObjectOutputStream(fos);
        oos.writeObject(gfg_g1);    // writeObject() method on Account class will be automatically called by jvm

        FileInputStream fis = new FileInputStream("abc.ser");
        ObjectInputStream ois = new ObjectInputStream(fis);
        GfgAccount gfg_g2 = (GfgAccount) ois.readObject();
        System.out.println("Username :" + gfg_g2.username + "  Password :" + gfg_g2.pwd);
    }
}
```

![default-serialization-deserialization](https://github.com/arpit04tripathi/files-cdn/raw/cdn/java/marker-interface/default-serialization-deserialization.png)

### Suppose super class of a new class implement Serializable interface, how can you avoid new class to being serialized?
* Child class is already Serializable here and we ***can not unimplemented it***. 
* To avoid Java serialization you need to ***implement writeObject() and readObject() method*** in your Class and need to throw **NotSerializableException** from those method.

### Which methods are used during Serialization and DeSerialization process in Java?
* Java Serialization is done by java.io.ObjectOutputStream class. That class is a filter stream which is wrapped around a lower-level byte stream to handle the serialization mechanism.
* Store via serialization - `ObjectOutputStream.writeObject(saveThisobject)`. 
* Deserialize - `ObjectInputStream.readObject()`.

### Suppose you have a class which you serialized it and stored in persistence and later modified that class to add a new field. What will happen if you deserialize the object already serialized?
* If we don't provide **serialVersionUID** in our code java compiler will generate it and normally it’s [equal to hashCode of object](https://javarevisited.blogspot.com/2011/02/how-to-write-equals-method-in-java.html){:target="_blank"}.
* In this case Java Serialization API will throw **java.io.InvalidClassException** and this is the reason its recommended to have your own serialVersionUID in code and make sure to keep it same always for a single class.

```java
ANY-ACCESS-MODIFIER static final long serialVersionUID = 42L;
```

### What are the compatible changes and incompatible changes in Java Serialization Mechanism?
* Main challenge of changing a class is because of already serialized objects of that class and reconstructing them.
* As per Java Serialization specification
    - adding any field or method comes under compatible change 
    - changing class hierarchy or UN-implementing Serializable interfaces are non compatible changes.

### Can we transfer a Serialized object vie network?
* ***Yes***, you can transfer a Serialized object via network as serialized object remains in form of bytes. 
* You can also store serialized object in Disk or database as Blob.

### Which kind of variables is not serialized during Java Serialization?
* Java Serialization only persist state of object and not object itself.
* ***static*** variables - belong to the class and not to an object.
* **transient** variables - not included in java serialization process.

### If you don't store values of these variables then what would be value of these variable once you deserialize and recreate those objects?
- We get the ***default values*** of the object.
- Example: In case of static String or transient String, you will get NULL value of variable after deserializaton.

# Externalization
```java
public class User implements Externalizable {
    private String userName;
    private int age;
    public User() {} // there must a no argument constructor.
    public User(String userName, int age) {
        this.userName = userName;
        this.age = age;
    }
    @Override
    public void readExternal(ObjectInput in) throws IOException, ClassNotFoundException {
        userName = (String) in.readObject();
        age = in.readInt();
    }
    @Override
    public void writeExternal(ObjectOutput out) throws IOException {
        out.writeObject(userName);
        out.writeInt(age);
    }
    // Getters and Setter for member variables
}
```
- By Externalizable interface java developer has complete control on java class persistence.
- Only those fields will be persisted as byte stream which will be saved by *writeExternal* method, Other field in the class will not be externalized.

### serialVersionUID is a static variable and “We cannot serialize static variables”. How does it store serialversionuid?
* Yes, ***this is an exception***. Inspite of serialVersionUid being static, it get serialized.
* ObjectOutputStream writes every time to output stream and ObjectInputStream reads it back and if it does not have same values as in current version of class then it throw InvalidClassException.
