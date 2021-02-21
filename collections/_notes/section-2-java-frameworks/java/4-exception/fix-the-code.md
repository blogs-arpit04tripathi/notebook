---
layout: post
title: Fix the Code
permalink: /:collection/java/exceptions/fix-the-code
---

- TOC
{:toc}

<hr><br>

# Fix the code - Q1
```java
public class TestException {
    public static void main(String[] args) {
        try {
            testExceptions();
        } catch (FileNotFoundException | IOException e) {
            e.printStackTrace();
        }
    }
    public static void testExceptions() throws IOException, FileNotFoundException {}
}
```
**Compilation error**
* exception FileNotFoundException is already caught by the alternative IOException
* FileNotFoundException is subclass of IOException

**Fix**
* Keep only IO Exception
* Catch first FileNotFoundException and then IOException 

# Fix the code - Q2
```java
public class TestException1 {
  public static void main(String[] args) {
    try {go();}
    catch (IOException e) { e.printStackTrace();}
    catch (FileNotFoundException e) { e.printStackTrace();}
    catch (JAXBException e) { e.printStackTrace(); }
  }
  public static void go() throws IOException, JAXBException, FileNotFoundException{}
}
```
**Compilation Error**
* Unreachable catch block for FileNotFoundException. It is already handled by the catch block for IOException

# Fix the code - Q3
```java
public class TestException2 {
  public static void main(String[] args) {
    try {foo();}
    catch (IOException e) { e.printStackTrace();}
    catch(JAXBException e){ e.printStackTrace();}
    catch(NullPointerException e){ e.printStackTrace();}
    catch(Exception e){ e.printStackTrace(); }
  }
  public static void foo() throws IOException{}
}
```
**Compilation error**
* “Unreachable catch block for JAXBException. This exception is never thrown from the try statement body”
* JAXBException is a checked exception, must be in throws.
catching NullPointerException is valid, unchecked exception

**Fix**
* remove the catch block of JAXBException

# Fix the code - Q4
```java
public class TestException3 {
  public static void main(String[] args) {
    try{bar();    }
    catch(NullPointerException e){ e.printStackTrace();}
    catch(Exception e){ e.printStackTrace();}
    foo();
  }
  public static void bar(){}
  public static void foo() throws NullPointerException{}
}
```
* trick question, there is no problem with the code and it will compile successfully.
* can always catch Exception or any unchecked exception even if it’s not in the throws

# Fix the code - Q5
```java
public class TestException4 {
	public void start() throws IOException{    }
	public void foo() throws NullPointerException{}
}
class TestException5 extends TestException4{
	public void start() throws Exception{}
	public void foo() throws RuntimeException{}
}
```
**Compilation Error**
* won’t compile, start() signature is not same in subclass.
* IOException => Exception not allowed, can be restrictive checked exception only.

**Fix**
* either change method signature to be same superclass
* remove throws clause from subclass.

# Fix the code - Q6
```java
public class TestException6 {
    public static void main(String[] args) {
        try {
            foo();
        } catch (IOException | JAXBException e) {
            e = new Exception("");
            e.printStackTrace();
        } catch (Exception e) {
            e = new Exception("");
            e.printStackTrace();
        }
    }
    public static void foo() throws IOException, JAXBException {}
}
```
**Compilation Error**
* **object in catch block is final, can’t change it’s value**.
* The parameter e of a multi-catch block cannot be assigned.

# Fix the code - Q7
```java
public static void start() {
    System.out.println("Programmers");
}
public static void main(String args[]) {
    try {
        start();
    } catch (IOException ioe) {
        ioe.printStackTrace();
    }
}
```
**Compilation error**
* IOException is a checked Exception and start() method doesn't throw IOException
* Exception java.io.IOException is never thrown in body of corresponding try statement

# Fix the code - Q8
```java
public class SuperClass {
    public void start() throws IOException {
        throw new IOException("Not able to open file");
    }
}
public class SubClass extends SuperClass {
    public void start() throws Exception {
        throw new Exception("Not able to start");
    }
}
```
**Compilation Error**
* Override, checkedException a subclass of it
* IOException or any sub class of IOException but not super class of it e.g. Exception.

# Fix the code - Q9
```java
public static void start() throws IOException, RuntimeException {
    throw new RuntimeException("Not able to Start");
}
public static void main(String args[]) {
    try {
        start();
    } catch (Exception ex) {
        ex.printStackTrace();
    } catch (RuntimeException re) {
        re.printStackTrace();
    }
}
```
**Compilation error**
* exception java.lang.RuntimeException has already been caught.
* Exception is super class of RuntimeException.