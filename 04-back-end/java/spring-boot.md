# Spring Boot

Spring applications usually require a lot of setup. Consider working with JPA \(Datasource, TransactionManager, EntityManagerFactory, etc\) or Web MVC application \(WebApplicationInitializer/web.xml, ContextLoaderListener, DispatcherServlet\). Spring boot can be thought of as an enhancement over Spring, that can do most of this setup itself.

Spring Boot is an opinionated runtime for Spring projects using sensible defaults mostly based on classpath contents, that handles most low-level and predictable setup.

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
All you need is 3 files: pom.xml, Controller and Application launcher.

Navigate to http://start.spring.io/
Make selections and download a zip file
It scaffolds the project for you!

http://localhost:8080/env

Reference Links
---------------
https://docs.spring.io/spring-boot/docs/current/reference/html/common-application-properties.html
```



