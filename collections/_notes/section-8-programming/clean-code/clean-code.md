---
layout: post
title: Clean Code
permalink: /:collection/clean-code
---

- TOC
{:toc}

---

# What is Clean Code?
- Clean code is focused.
  - Each function, each class, each module exposes a single-minded attitude that remains entirely undistracted, and unpolluted, by the surrounding details.
- Write one method that says more clearly what it does, and some submethods saying how it is done.
- clean code when each routine you read turns out to be pretty much what you expected.

# Meaningful Names
- Use Intention-Revealing Names
- Length of a name should correspond to the size of its scope.

> One difference between a smart programmer and a professional programmer is that the professional understands that clarity is king. Professionals use their powers for good and write code that others can understand.

> We want our code to be a quick skim, not an intense study. 

## Class Names
- Classes and objects should have noun or noun phrase names like Customer, WikiPage, Account, and AddressParser.
- A class name should not be a verb.
  - Avoid words like Manager, Processor, Data, or Info in the name of a class.
- When constructors are overloaded, use static factory methods with names that describe the arguments.

```java
Complex fulcrumPoint = Complex.FromRealNumber(23.0); 
```

## Method Names
- Should have verb or verb phrase names like postPayment, deletePage, or save.
- Accessors, mutators, and predicates should be named for their value and prefixed with get, set, and is according to the javabean standard.
- **Pick One Word per Concept**
  - Pick one word for one abstract concept and stick with it.
  - For instance, it’s confusing to have fetch, retrieve, and get as equivalent methods of different classes.

# Functions
- should be small.
- Functions should hardly ever be 20 lines long.
- blocks within if, else, while and so on should be one line long.
  - Probably that line should be a function call.
- The indent level of a function should not be greater than one or two.

>FUNCTIONS SHOULD DO ONE THING.
THEY SHOULD DO IT WELL.
THEY SHOULD DO IT ONLY.

- One Level of Abstraction per Function.
- Be consistent in your names. Use the same phrases, nouns, and verbs in the function names you choose for your modules.
  - Example - the names includeSetupAndTeardownPages, includeSetupPages, includeSuiteSetupPage, and includeSetupPage.

## Function Arguments - max 3.
- Difficult for Unit testing all combinations of parameters.
- One input argument is the next best thing to no arguments.
- Flag Arguments
  - Passing a boolean into a function is a truly terrible practice.
  - It immediately complicates the signature of the method, loudly proclaiming that this function does more than one thing.
    - It does one thing if the flag is true and another if the flag is false!
  - method call render(true) is just plain confusing to a poor reader.
  - We should have split the function into two: renderForSuite() and renderForSingleTest().
- pg 72
- 