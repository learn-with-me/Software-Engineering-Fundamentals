# Java in Heroku

##### Setup verification

```
Java 8     : java -version
Maven 3    : mvn -version
Git        : git --version
```

##### Configuration

```
pom.xml
=======
Heroku recognizes an app as Java by the existence of pom.xml file in the root directory.
Heroku reads this file and installs the dependencies using the mvn clean install command.
The Maven process compiles and build a JAR, with dependencies, placing it into your application’s target directory.
This process is accomplished with the spring-boot-maven-plugin in the pom.xml.
If not using Spring in app, you can accomplish this with the plugin configuration "maven-assembly-plugin" in pom.xml.

system.properties
Determines the version of Java to use (Heroku supports many different versions).

application.properties
DB info, PORT, etc

Create custom pom.xml by
mvn archetype:create
```

##### Heroku config

```
Access config by
System.getenv().get("ENERGY");
OR
System.getenv("JDBC_DATABASE_URL");
```

##### Database

```
It is not recommended to copy this value into a static file since the environment may change the value. Instead an
application should read the DATABASE_URL environment variable (or JDBC_DATABASE_URL variable described later) and
set up the database connections based on that information.

JDBC_DATABASE_URL
The official Heroku buildpacks for Java, Scala, Clojure, and Gradle will attempt to create a JDBC_DATABASE_URL
environment variable when a dyno starts up. This variable is dynamic and will not appear in your list of configuration
variables when running heroku config. You can view it by running the following command:

heroku run echo \$JDBC_DATABASE_URL
heroku run echo \$JDBC_DATABASE_USERNAME
heroku run echo \$JDBC_DATABASE_PASSWORD

SPRING_DATASOURCE_URL
The official Heroku buildpacks for Java and Gradle will attempt to create SPRING_DATASOURCE_URL,
SPRING_DATASOURCE_USERNAME, and SPRING_DATASOURCE_PASSWORD environment variables when a dyno starts up. The values of
the variables will be identical to the values in the corresponding JDBC variables.

https://devcenter.heroku.com/articles/getting-started-with-java#use-a-database
https://devcenter.heroku.com/articles/connecting-to-relational-databases-on-heroku-with-java
```



