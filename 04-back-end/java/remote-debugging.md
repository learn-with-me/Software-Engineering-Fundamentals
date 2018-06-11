# Remote Debugging

Add the following command line, after the 'java' but before app-specific args

```
-Xdebug -Xrunjdwp:server=y,transport=dt_socket,address=8000,suspend=n

Example
java -jar app.jar

Would become
java -Xdebug -Xrunjdwp:server=y,transport=dt_socket,address=8000,suspend=n -jar app.jar

-Xdebug    enables debugging capabilities in the JVM
-Xrunjdwp  loads the JPDA reference implementation of JDWP
```



#### Explanation of Command line params

```
https://docs.oracle.com/cd/E13150_01/jrockit_jvm/jrockit/jrdocs/refman/optionX.html
```



