# Monitoring

Monitoring gives us the ability to observe our system's state and address issues before they impact our business. Monitoring can also help to optimize our users' experience.

To analyze the data, first, you need to extract metrics from your system - like the Memory usage of a particular application instance. We call this extraction instrumentation.

We use the term white box monitoring when metrics are provided by the running system itself. Every service is different, and you can monitor many aspects of them. Metrics can range from low-level resources like Memory usage to high-level business metrics like the number of signups. The four signals to know:

* **Error Rate:** Because errors are user facing and immediately affect your customers.
* **Response time:** Because the latency directly affects your customers and business.
* **Throughput:** The traffic helps you to understand the context of increased error rates and the latency too.
* **Saturation:** It tells how "full" your service is. If the CPU usage is 90%, can your system handle more traffic?

### Instrumentation

In many cases, instrumentation means adding extra logic and code pieces that come with a performance overhead. You can instrument your system manually, but most of the paid monitoring solutions provide out of the box instrumentations.

Instrumentations can be very specific and usually need expertise and more development time. Also, a bad instrumentation can introduce bugs into your system or generate an unreasonable performance overhead. Instrumenting your code can also produce a lot's of extra lines and bloat your applications codebase.

### Picking your Node.js Monitoring Tool

* **Expertise:** Do you have the expertise? Building a monitoring tool and writing a high-quality instrumentation and extracting the right metrics is not easy. You need to know what you are doing.
* **Build or buy:** Building a proper monitoring solution needs lot's of expertise, time and money while obtaining an existing solution can be easier and cheaper.
* **SaaS or on-premises:** Do you want to host your monitoring solution? Can you use a SaaS solution, what's your data compliance and protection policy? Using a SaaS solution can be a good pick for example when you want to focus on your product instead of tooling. Both open-source and commercial solutions are usually available as hosted or on-premises setup.
* **Licensing:** Do you want to ship your monitoring toolset with your product? Can you use a commercial solution? You should always check licensing.
* **Integrations:** Does it support my external dependencies like databases, orchestration system and npm libraries?
* **Instrumentation:** Does it provide automatic instrumentation? Do I need to instrument my code manually? How much time would it take to do it on my own?
* **Microservices:** Do you build a monolith or a distributed system? Microservices needs specific tools and philosophy to debug and monitor them effectively. Do you need to distribute tracing or security checks?

### Node Monitoring with Prometheus

Prometheus is an open-source solution for Node.js monitoring and alerting. It provides powerful data compressions and fast data querying for time series data.

> Time series is a stream of immutable timestamped values that belong to the same metric and the same labels. The labels cause the metrics to be multi-dimensional.

#### Data collection and metrics types

Prometheus uses the HTTP pull model, which means that every application needs to expose a GET /metrics endpoint that can be periodically fetched by the Prometheus instance. Prometheus has four metrics types:

* **Counter:** cumulative metric that represents a single numerical value that only ever goes up
* **Gauge:** represents a single numerical value that can arbitrarily go up and down
* **Histogram:** samples observations and counts them in configurable buckets
* **Summary:** similar to a histogram, samples observations, it calculates configurable quantiles over a sliding time window

#### Monitoring a Node.js application

When we want to monitor our Node.js application with Prometheus, we need to solve the following challenges:

* **Instrumentation:** Safely instrumenting our code with minimal performance overhead
* **Metrics exposition:** Exposing our metrics for Prometheus with an HTTP endpoint
* **Hosting Prometheus:** Having a well configured Prometheus running
* **Extracting value:** Writing queries that are statistically correct
* **Visualizing:** Building dashboards and visualizing our queries
* **Alerting:** Setting up efficient alerts
* **Paging:** Get notified about alerts with applying escalation policies for paging



### References

```
https://blog.risingstack.com/node-js-performance-monitoring-with-prometheus/
```



