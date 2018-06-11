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
    • server=y means listen for a debugger application to attach
    • transport-dt_socket is the name of the transport to use in connecting to debugger
    • address=8000 means listen for a connection at this address (no host = this port on add interfaces)
    • suspend=n means do not wait for a debugger to attach
```

#### Explanation of Command line params

```
https://docs.oracle.com/cd/E13150_01/jrockit_jvm/jrockit/jrdocs/refman/optionX.html
```

#### References

```
https://coderwall.com/p/8f-xga/remote-debugging-a-java-application
https://stackify.com/java-remote-debugging/
```



