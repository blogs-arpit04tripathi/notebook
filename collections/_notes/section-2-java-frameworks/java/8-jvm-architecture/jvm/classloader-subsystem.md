---
layout: post
title: ClassLoader Subsystem
permalink: /:collection/java/jvm/classloader-subsystem
---

- Responsible for locating and importing the binary data for classes.
- Activities are performed in a strict order:
    1. **Loading**: finding and importing the binary data for a type
    2. **Linking**: performing verification, preparation, and (optionally) resolution
       1. ***Verification***: ensuring the correctness of the imported type
       2. ***Preparation***: allocating memory for class variables and initializing the memory to default values
       3. ***Resolution***: transforming symbolic references from the type into direct references.
    3. **Initialization**: invoking Java code that initializes class variables to their proper starting values.

![jmm-diagram]({{site.cdn}}/java/jvm-architecture/classloader-subsystem.png)

# 1. Loading
- Java run time system are independent of file systems because of classloaders.
- Java classes aren’t loaded into memory all at once, but when required by an application.
  - Java ClassLoader is called by the JRE and these ClassLoaders load classes into memory dynamically.

**A Java Classloader is of three types:**
1. **BootStrap ClassLoader**
   - **Primodial ClassLoader**.
     - loads classes from the location rt.jar.
     - doesn’t have any parent ClassLoaders.
   - A Bootstrap Classloader is a Machine code which kickstarts the operation when the JVM calls it.
   - It is not a java class.
   - Its job is to load the first pure Java ClassLoader.
2. **Extension ClassLoader**
   - Child of Bootstrap ClassLoader 
   - Loads the extensions of core java classes from the respective JDK Extension library.
   - It loads files from jre/lib/ext directory or any other directory pointed by the system property java.ext.dirs.
3. **Application ClassLoader**
   - ***System ClassLoader***.
   - child class of Extension ClassLoader.
   - loads the Application type classes found in the environment variable CLASSPATH, -classpath or -cp command line option.

**Classloader principles**
- **Delegation**
   - ***ClassLoader Delegation Hierarchy Model*** `Application ClassLoader --> Extension ClassLoader --> Bootstrap ClassLoader`.
   - Bootstrap ClassLoader is always given the higher priority.
- **Visibility**
  - Application classloader can see the classes loaded by the parent classloaders but not vice-versa.
  - ClassNotFoundException at runtime.
- **Uniqueness**
  - Class loaded by the parent classloader should not be again loaded by the child classloader.

![jmm-diagram]({{site.cdn}}/java/jvm-architecture/classloader-subsystem-loading.png)

**Static vs Dynamic Class Loading**
- **Static class loading**
  - classes are statically loaded via the new operator.
  - initializes the object after loading it.
- **Dynamic class loading**
  - classes are programmatically loaded by using the Class.forName() or the loadClass() method.
  - only loads the class but doesn’t initialize the object.

# 2. Linking
- performs the linking of a class or an interface.
- Involves the allocation of new data structures, it may throw the ***OutOfMemoryError***.
- Performs the three important activities:
  - **Verification**
    - process of checking the binary representation of a class
    - validating whether the generated .class file is valid or not.
    - performed by the Bytecode verifier and if the generated .class file is not valid, a **VerifyError** is thrown.
  - **Preparation**
    - process of assigning the memory for the class level or interface level static variables and assigns the default values.
  - **Resolution**
    - process of changing the symbolic references with the original memory references from the method area.

# 3. Initialization
- performs the final phase of the class loading.
- all the static variables are assigned the original values and the static blocks are executed from the parent to the child class.
- requires careful synchronization as JVM is multithreaded and some threads may try to initialize the same class or interface at the same time.
