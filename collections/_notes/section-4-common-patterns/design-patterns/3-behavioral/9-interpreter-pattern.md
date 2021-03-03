---
layout: post
title: Interpreter Pattern
permalink: /:collection/design-patterns/behavioral/interpreter-pattern
---

- TOC
{:toc}

<hr><br>

-	This is used to define a grammatical representation for a language and provides an interpreter to deal with this grammar.
-	The best example of this pattern is java compiler that interprets the java source code into byte code that is understandable by JVM. Google Translator is also an example of interpreter pattern where the input can be in any language and we can get the output interpreted in another language.

To implement interpreter pattern
- we need to create Interpreter context engine that will do the interpretation work 
- then we need to create different Expression implementations that will consume the functionalities provided by the interpreter context.
- Finally we need to create the client that will take the input from user and decide which Expression to use and then generate output for the user.

# Example-Interpreter Pattern
- user input will be of two forms – “\<Number> in Binary” or “\<Number> in Hexadecimal” and
- our interpreter client should return it in format “\<Number> in Binary= \<Number_Binary_String>” and “\<Number> in Hexadecimal= \<Number_Hex_String>” respectively.

![]({{site.cdn}}/design-patterns/behavioral-interpreter.png)

```java
public class InterpreterContext { 
    public String getBinaryFormat(int i){return Integer.toBinaryString(i);}     
    public String getHexadecimalFormat(int i){return Integer.toHexString(i);}
}
```
```java
public interface Expression {  String interpret(InterpreterContext ic);}
```
```java
public class IntToBinaryExpression implements Expression { 
    private int i;     
    public IntToBinaryExpression(int c){this.i=c;}
    @Override
    public String interpret(InterpreterContext ic){return ic.getBinaryFormat(this.i);} 
}
```
```java
public class IntToHexExpression implements Expression { 
    private int i;     
    public IntToHexExpression(int c){ this.i=c; }     
    @Override
    public String interpret(InterpreterContext ic) { return ic.getHexadecimalFormat(i); } 
}
```

```java
public class InterpreterClient { 
    public InterpreterContext ic;     
    public InterpreterClient(InterpreterContext i){ this.ic=i; }     
    public String interpret(String str){
        Expression exp=null;
        //create rules for expressions
        if(str.contains("Hexadecimal")){
         exp=new IntToHexExpression(Integer.parseInt(str.substring(0,str.indexOf(" "))));
        }else if(str.contains("Binary")){
         exp=new IntToBinaryExpression(Integer.parseInt(str.substring(0,str.indexOf(" "))));
        }else return str;         
        return exp.interpret(ic);
    }
     
    public static void main(String args[]){
        String str1 = "28 in Binary";
        String str2 = "28 in Hexadecimal";         
        InterpreterClient ec = new InterpreterClient(new InterpreterContext());
        System.out.println(str1+"= "+ec.interpret(str1));
        System.out.println(str2+"= "+ec.interpret(str2)); 
    }
}
```

# Important Points Interpreter Pattern
-	Interpreter pattern can be used when we can create a syntax tree for the grammar we have.
-	Interpreter pattern requires a lot of error checking and a lot of expressions and code to evaluate them, it gets complicated when the grammar becomes more complicated and hence hard to maintain and provide efficiency.

# JDK Example-Interpreter Pattern
java.util.Pattern and subclasses of java.text.Format are some of the examples of interpreter pattern used in JDK.
