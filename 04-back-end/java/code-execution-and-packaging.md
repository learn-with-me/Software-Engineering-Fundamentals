# Code Execution & Packaging

##### Verification

```
javac -version       # Compiler version
javac -help          # Display all compiler options
java -verbose        # Output compiler messages
java -deprecated     # Identify deprecated APIs

java -version        # Interpreter version
java -help           # Display interpreter options
java -verbose        # Display interpreter information
```

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

##### 



