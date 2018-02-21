# Configuration

##### Actuator End-points

```
App Config:   /autoconfig, /beans, /env, /configprops
App Info:     /health, /info, /metrics, /logfile (logging.file and logging.path)
Web Apps:     /mappings, /trace
Other:        /shutdown, /flyway, /liquibase

Unsecured Access
$ curl localhost:8080/health
$ curl localhost:8080/metrics

Disk Health
$ curl -u user:pa$s localhost:8080/health

Beans
$ curl -u user:c654eed6-b877-4494-8fb2-8e9fb21f00c4 localhost:8080/beans
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

Setting Required Authentication Credentials & Authorization Roles
security.user.name=admin
security.user.password=admin$ecret
management.security.role=ADMIN

Disable All Security Checks for Actuator Endpoints (behind firewall)
management.security.enabled=false
```



