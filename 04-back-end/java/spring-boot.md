# Spring Boot

Java application framework

##### Features

* Enables building production ready applications quickly \(RAD\).
* Provides common non-functional features as part of boilerplate:
  * Embedded servers: Tomcat, Jetty or Undertow
  * Metrics
  * Health checks: Spring Boot Actuator
  * Externalized configuration
  * Security, Caching, etc
* Quick starter projects with Auto Configuration: Web and JPA \(Java Persistence API with Hibernate\)
  * Uses Annotations to keep the code clean. Also known as Dependency Injection or Autowiring.
  * Looks at Frameworks available on the CLASSPATH
  * Looks at existing configuration for the application
  * Data access and configuration management
  * Controller integration through MVC
* Aspecting adds common behavior to a class at runtime or compile time
* Application Context is the heart. A bean factory. Serving at runtime.

##### Plugins

```
Web        - If you need embedded Tomcat and Spring MVC
Actuator   - Metrics
DevTools   - Hot reload+

YAML - replace application.properties to make it useful for production ready applications
```

##### Creating a project

```
Navigate to http://start.spring.io/
Make selections and download a zip file
It scaffolds the project for you!

http://localhost:8080/env

Reference Links
---------------
https://docs.spring.io/spring-boot/docs/current/reference/html/common-application-properties.html
```



