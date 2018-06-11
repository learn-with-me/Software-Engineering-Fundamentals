# Scala in Heroku

##### Setup Verification

```
Install sbt (Scala Dependency Manager)
brew install sbt@1
```

##### Configuration

```
Procfile
web: target/universal/stage/bin/play-getting-started -Dhttp.port=${PORT}

build.sbt
Heroku recognizes an app as Scala by the existence of a build.sbt file in the root directory.
The build.sbt file specifies dependencies that should be installed with your application.
When an app is deployed, Heroku reads this file and installs the dependencies using the sbt compile stage command.

system.properties
Determines the version of Java to use.

config
scala.util.Properties.envOrElse("ENERGY", "12 GeV")
```

##### Execution

```
sbt compile stage
Run in your local directory to install the dependencies, preparing your system for running the app locally.
```



