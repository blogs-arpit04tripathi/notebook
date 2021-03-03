---
layout: post
title: Prototype Pattern
permalink: /:collection/design-patterns/creational/prototype-pattern
---

- TOC
{:toc}

<hr><br>

# Prototype Pattern
-	Used when ***Object creation is a costly affair*** and requires a lot of time and resources, and a ***similar object already exists***. 
-	Provides a ***copy mechanism from original to new, and then modify it***. 
-	Uses java cloning to copy the object hence ***object should be clonable***.
-	However, whether to use shallow or deep copy depends on the requirements and its a design decision.

```java
public class Employees implements Cloneable {
    private List<String> empList;

    public Employees() {
        empList = new ArrayList<String> ();
    }

    public Employees(List<String> list) {
        this.empList = list;
    }

    public void loadData() {
        //read all employees from database and put into the list
        empList.add("Pankaj");
        empList.add("Raj");
        empList.add("David");
        empList.add("Lisa");
    }

    public List<String> getEmpList() {
        return empList;
    }

    @Override
    public Object clone() throws CloneNotSupportedException {
        List<String> temp = new ArrayList<String> ();
        for (String s: this.getEmpList()) {
            temp.add(s);
        }
        return new Employees(temp);
    }
}
```
```java
public class TestPrototypePattern {
    public static void main(String[] args) throws CloneNotSupportedException {
        Employees emps = new Employees();
        emps.loadData();
        //Use the clone method to get the Employee object
        Employees empsNew = (Employees) emps.clone();
        Employees empsNew1 = (Employees) emps.clone();
        List<String> list = empsNew.getEmpList();
        list.add("John");
        List<String> list1 = empsNew1.getEmpList();
        list1.remove("Pankaj");
        System.out.println("emps List: " + emps.getEmpList());
        System.out.println("empsNew List: " + list);
        System.out.println("empsNew1 List: " + list1);
    }
}
```