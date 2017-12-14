# Java

Java is a static, compiled language

> PATH: This is a concept within Operating System, and not Java. It refers to the path where libraries are found. JDK Home must be added to PATH to have javac and java accessible via command line. Steps to setup PATH are mentioned in JAVA setup instructions.
>
> CLASSPATH is the path where jvm should be able to find all the classes. Classpath is the path or list of directory which is used by ClassLoaders to find and load class in Java program. Located in META-INF/manifest.mf file inside JAR file in Java.  
> [http://javarevisited.blogspot.sg/2011/01/how-classpath-work-in-java.html](http://javarevisited.blogspot.sg/2011/01/how-classpath-work-in-java.html)

##### Local Code execution

```
via Command Line
> java -cp <target_directory> <compiled_class_name>
> java -cp target/classes/ problems.wordCount.WordCount
> java -cp "target/classes/;lib/log4j.jar" problems.wordCount.WordCount        // with external jar
> java -classpath target/classes/ problems.wordCount.WordCount

via Maven
> mvn exec:java -Dexec.mainClass=<Filename_with_package>
> mvn exec:java -Dexec.mainClass="problems.wordCount.WordCount"
```

##### Jar Handling

```
Java Application Archive
Package java files for a core java app. Its just a zip file with compressed files and no additional configuration.

> jar -tvf HelloWorld.jar                     // View contents of a jar file
> jar -xvf HelloWorld.jar                     // Extracting contents of a jar file
> jar -cvf HelloWorld.jar HelloWorld.class
> java -jar HelloWorld.jar                    // Executing jar program from jar archive
        For jar to be executable, it must have main-class entry in MANIFEST.mf
```

##### War file

```
Web Application Archive
Package all files with a specific structure and deploy it to any Java Web/Application server. Compressed.
Contains web.xml in WEB-INF folder
```

##### Ear file

```
Enterprise Java Archive
Package all files with a specific structure. Same as war + can include EJBs and deploys to an Application Server.
Can contain multiple JAR/WAR files. Contains application.xml in META-INF folder.
Applications containing EJBs will also have ejb-jar.xml in the same META-INF folder.
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
Setup and local code execution
Basics
    Data Types
    Access Modifiers
Collection
```



