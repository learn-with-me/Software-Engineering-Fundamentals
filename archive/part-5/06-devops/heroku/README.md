# Heroku

#### Learning

```
https://devcenter.heroku.com
```

##### Dyno

```
Applications run in a collection of lightweight containers called Dynos. These are isolated, virtualized unix
containers that provide environment required to run an application

Every Dyno belongs to one of the three configurations

Web: Only web dynos receive HTTP traffic from the routers.

Worker: Of any process type declared in Procfile, other than “web”. Typically used for background jobs, queueing systems
and timed jobs. You can have multiple kinds of worker dynos in your application. For example, one for urgent jobs and
another for long-running jobs.
https://devcenter.heroku.com/articles/background-jobs-queueing

One-Off: Temporary dynos that can run detached, or with their input/output attached to your local terminal. They’re
loaded with your latest release. They can be used to handle administrative tasks, such as database migrations and
console sessions. They can also be used to run occasional background work, as with Heroku Scheduler. 
https://devcenter.heroku.com/articles/one-off-dynos
https://devcenter.heroku.com/articles/scheduler
```

##### Provision Add-ons

```
Third-party cloud services that provide out-of-the-box additional services for your application, from persistence
through logging to monitoring and more.

By default, Heroku stores 1500 lines of logs from your application. However, it makes the full log stream available as
a service - and several add-on providers have written logging services that provide things such as log persistence,
search, and email and SMS alerts.

Papertrail
https://devcenter.heroku.com/articles/papertrail
```

##### Additional Concepts

```
Logging         - https://devcenter.heroku.com/articles/logging
HTTP Routing    - https://devcenter.heroku.com/articles/http-routing
Dyno            - https://devcenter.heroku.com/articles/dynos

Everything else
https://devcenter.heroku.com/articles/buildpacks

TODO
https://devcenter.heroku.com/articles/node-websockets
https://tools.ietf.org/html/rfc6455
https://devcenter.heroku.com/articles/mean-apps-restful-api
```



