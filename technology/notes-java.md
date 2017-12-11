# Java

> PATH: This is a concept within Operating System, and not Java. It refers to the path where libraries are found. JDK Home must be added to PATH to have javac and java accessible via command line. Steps to setup PATH are mentioned in JAVA setup instructions.
>
> CLASSPATH is the path where jvm should be able to find all the classes. Classpath is the path or list of directory which is used by ClassLoaders to find and load class in Java program. Located in META-INF/manifest.mf file inside JAR file in Java.  
> http://javarevisited.blogspot.sg/2011/01/how-classpath-work-in-java.html

##### Local Code execution

```
via Command Line
> java -cp <target_directory> <compiled_class_name>
> java -cp target/classes/ problems.wordCount.WordCount
> java -classpath target/classes/ problems.wordCount.WordCount

via Maven
> mvn exec:java -Dexec.mainClass=<Filename_with_package>
> mvn exec:java -Dexec.mainClass="problems.wordCount.WordCount"
```

##### Jar Handling

```
> jar -tvf HelloWorld.jar                     // View contents of a jar file
> jar -xvf HelloWorld.jar                     // Extracting contents of a jar file
> jar -cvf HelloWorld.jar HelloWorld.class
> java -jar HelloWorld.jar                    // Executing jar program from jar archive
        For jar to be executable, it must have main-class entry in MANIFEST.mf
```

##### Index

```
Setup and local code execution
Basics
    Data Types
    Access Modifiers
Collection
```



