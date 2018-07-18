# Java

> Disclaimer: If you happen to do not understand a term, take note of it. I may have explained it in detail in later sections.

I am trying to think how to best express what Java is. Its' not just a language with JVM \(atleast that's what I didn't knew for several years\). Here I'll break it down for you. On a higher level, Java serves as a language as well as a software platform \(don't tell me I know you're talking about JDK, coz there is more than that\)

## Java as a Software Platform

Java platform is a collection of software components which allow development and execution of byte-code based languages \[WHAT????\]. Bytecode is binary code that the Java platform interprets. It is crucial to pick and choose the right configuration of the platform for the kind of work you are going to do. For example, the platform is available in four flavors \[WHY\].

1. Java Card - used in smart cards and small memory devices.
2. Java ME \(Micro Edition\) - used in personal digital assistant, setup box and printer applications
3. Java SE \(Standard Edition\) - used in development of desktop, communication, user interface based applications.
4. Java EE \(Enterprise Edition\) - used in web-based development, messaging, distributed and enterprise applications

Platform has support for many languages such as - Java, Jython, Jruby, Scala, Groovy, Kotlin, Rakudo Perl 6 \[WHAT DOES THIS MEAN?? NOT JUST JAVA??\]

#### JRE \(Java Runtime Environment\)

The minimum environment required to run a java program. JRE is composed of following components:

1. Interpreter - it understands binary java code
2. Tools - functionalities such as security, core services, internationalization, RMI, etc. Example \(keytool, rmiregistry, javacpl\)
3. Library - Java Application Programming Interface \(rt.jar, jce.jar, jsse.jar, etc\) \[WHAT DOES THIS MEAN???\] \[ELABORATE ALL\]

#### JDK \(Java Development Kit\)

The minimum environment required to develop a java program, also known as Java SE. JDK is composed of the following components:

1. Compiler - compiles java code into binary code
2. Interpreter - processes byte code to native code
3. Tools - functionality such as security, core services, internationalization, RMI, etc.
4. Library - Java Application Programming Interface \(rt.jar, jce.jar, jsse.jar, etc\) \[WHAT DOES THIS MEAN???\] \[ELABORATE ALL\]

## Java as a language

Java is a multi-paradigm programming language . It is one of the most used programming language for development of various types of software such desktop, enterprise, web and mobile applications. \[THINK OF ALL OTHER PLACES\].

#### Important Attributes

* **Statically typed** - type of the variable is known at compile time
* **Object oriented** - Object centered programming
* **Concurrent** - support for multi-threading
* **Reflective** - allows inspection of class, method, interface, fields

## Installation

> CLASSPATH is the path where jvm should be able to find all the classes. Classpath is the path or list of directory which is used by ClassLoaders to find and load class in Java program. Located in META-INF/manifest.mf file inside JAR file in Java.  
> [http://javarevisited.blogspot.sg/2011/01/how-classpath-work-in-java.html](http://javarevisited.blogspot.sg/2011/01/how-classpath-work-in-java.html)

You really should understand well, what PATH and CLASSPATH in Java mean.

\[OK, HOW DO I INSTALL IT NOW\] \[INSTALLING AND SETTING PATH ARE ITS OWN CHAPTER\]

#### PATH

This is a concept within Operating System, and not Java. An Operating System allows you to set key-value pairs, called Environment Variables, to be able to configure software or share information among multiple modules. Generally environment variables can be used to identify installation directory, location of temporary files, tools, profile setting, etc.

In terms of "path for Java", it refers to the path where Java libraries are found. JDK's bin folder must be added to PATH to have javac and java accessible via command line. Example "/java/jdk1.8.0\_65/bin".

Steps to setup PATH are mentioned in JAVA setup instructions. \[REALLY???\]

## Java Compiler and Interpreter

#### Compiler

Compilation process is what generates bytecode. Bytecode is binary code that is understood by the JVM.

#### Interpreter

It takes bytecode as input and executes the code by converting it into native code

---

##### Features - Java 8

```
forEach() method in Iterable interface
default and static methods in Interfaces
Functional Interfaces and Lambda Expressions
Java Stream API for Bulk Data Operations on Collections
Java Time API
Collection API improvements
Concurrency API improvements
Java IO improvements
Miscellaneous Core API improvements
```

##### JVM Languages

```
https://en.wikipedia.org/wiki/List_of_JVM_languages
https://blog.frankel.ch/rise-fall-jvm-languages/#gsc.tab=0
```

##### Java Shell

```
https://dzone.com/articles/jshell-finally-an-official-shell-in-java-9
http://www.crashub.org/
```

##### Index

```
About
Features
Setup and local code execution
Basics
    Data Types
    Access Modifiers
Collection
```

##### Terms

```
Entity    - Java object mapped to DB table, used to store and retrieve Data from DB using ORM tool
Hibernate - ORM (Object Relational Mapping) tool
H2        - Java based SQL Database
Compile time vs Runtime
```



