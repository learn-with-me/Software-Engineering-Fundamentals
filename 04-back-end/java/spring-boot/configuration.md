# Configuration

##### Actuator End-points

```
App Config:   /autoconfig, /beans, /env, /configprops
App Info:     /health, /info, /metrics, /logfile (logging.file and logging.path)
Web Apps:     /mappings, /trace
Other:        /shutdown, /flyway, /liquibase

Unsecured Access
$ curl localhost:8080/health

Disk Health
$ curl -u user:pa$s localhost:8080/health
```

##### Actuator properties - Enabling/Disabling

```
Enabling/Disabling Individual Endpoints:
endpoints.shutdown.enabled=true
endpoints.mappings.enabled=false
endpoints.trace.enabled=false

Global Enabling/Disabling Endpoints:
endpoints.enabled=false
endpoints.info.enabled=true

Enabling/Disabling Endpoints HTTP Access:
management.port=-1

Enabling/Disabling Endpoints JMX Access:
endpoints.jmx.enabled=false
```

##### Actuator properties - Configuration

```
Changing Security Requirements (Sensitivity):
endpoints.shutdown.sensitive=true
endpoints.mappings.sensitive=false
endpoints.trace.sensitive=false

Renaming Endpoints:
endpoints.beans.id=springbeans
endpoints.trace.id=httprequests
endpoints.trace.logfile=log
```



