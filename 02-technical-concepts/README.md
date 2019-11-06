### CS Fundamentals 101

> Just because you can do it with a language/framework, does not mean you should.

#### Application Development

* Traditional Approach \(Client-Server\)
* SOA Approach
* Virtualized SOA Approach \(Service Virtualization Layer\)
* Micro-service Approach
* Event-driven Systems
* Streaming Analytics Architecture
* CQRS

###### Event-driven Systems

**JMS** - you can send only 200-300 messages per second and then the queue gets full until some/all of the messages are processed.

**Kafka** - 

#### Scoring

* [https://www.joelonsoftware.com/2000/08/09/the-joel-test-12-steps-to-better-code/](https://www.joelonsoftware.com/2000/08/09/the-joel-test-12-steps-to-better-code/)

# More Ideas

```
Orchestration
RWD vs Adaptive vs Mobile Optimized

https://12factor.net/
```

#### Draft

```
Unit Testing
------------
https://www.toptal.com/java/a-guide-to-everyday-mockito

Mocks - used as a replacement for a dependency
Spies - creating a spy requires an instance to spy on. It’s spying on a real object.
Stubs

The need to use a spy to partially mock a class is an indicator that a class is doing too much, thus violating
    the single responsibility principle.

Mockito
    create a mock
    tell Mockito what to do when specific methods are called on it
    use the mock instance in your test instead of the real thing
After the test
    query the mock to see what specific methods were called
    or check the side effects in the form of changed state

import static org.mockito.Mockito.*;

Out of the box, Mockito cannot mock final classes and final or static methods.
If you really need it, Mockito 2 provides the experimental MockMaker plugin.
Also note that the methods equals() and hashCode() cannot be mocked.
```



