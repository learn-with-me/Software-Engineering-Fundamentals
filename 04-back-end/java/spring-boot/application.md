# Application

##### Glossary

```
@Component         - Found during classpath scanning and registered in the context as a Spring Bean
                     @Service, @Repository, @Controller are specializations of @Component, for more specific cases.
@ComponentScan     - Ensures that classes decorated with @Component are found and registered as Spring Beans.
                     It is already included in @SpringBootApplication
@Bean              - Serves similar purpose as of Component, just that it is not auto-detected. Methods decorated
                     with @Bean produce a bean to be managed by Spring container during configuration stage.

@Controller        - beans to handle incoming HTTP requests
@RestController    - ^
@RequestMapping    - To map HTTP requests uri patterns to methods in your controller
```



