# Heroku Basic Management

##### Login and App Management

```
heroku login   // Login
heroku apps    // To verify login and list all the apps on account
```

##### Dependency Mechanism

```
Varies across languages
Ruby    - Gemfile
Python  - requirements.txt
Node    - package.json
Java    - pom.xml
```

##### Procfile

    A text file in the root directory of your application, to explicitly declare what command should be executed to start
    your app.

    Example:
    `web: node --debug=5858 index.js`
    `web: java -jar target/java-getting-started-1.0.jar`
    `web: java -jar lib/foobar.jar $PORT`
    `queue: java -jar lib/queue-processor.jar`

    The name `web` is important here. It declares that this process type will be attached to the HTTP routing stack of
    Heroku, and receive web traffic when deployed. Procfiles can contain additional process types. For example, you might
    declare one for a background worker process that processes items off of a queue.

##### Deploy the App

```
heroku create            // Create a new app
git push heroku master   // Push & Deploy code to heroku

heroku info              // Display information about the app
heroku ps                // Check how many dynos are running
heroku ps:scale web=1    // Ensure atleast one instance of the app is running
heroku open              // Visit the app in browser
heroku open cool         // Open a path directly in browser
heroku logs --tail       // View the logs
heroku local             // Runs the app in local by examining the Procfile
heroku local -p 7000     // Runs the app in local at port 7000
heroku local web         // Runs the app in local executing web command
heroku restart           // Restart the app manually
heroku ps:restart        // Restart the app manually

http://localhost:5000/   // Default port is 5000

Release management
heroku releases          // Look at the history of releases
heroku releases:info v24 // Look at detailed info on a release
heroku rollback          // Rollback last release
heroku rollback v40      // Rollback to a certain version

Test your app deploy for Production
rm -rf node_modules
npm install --production
heroku local web
If it runs fine, you're all set and do not have any local dependencies

Commands
https://devcenter.heroku.com/articles/dynos
```

##### Pushing local changes

```
git remote -v            // Verify that git remote is set
heroku local             // Once you make code changes locally, test in local
git add .                // Add the modified files to local repository
git commit -m "Demo"     // Commit the changes
git push heroku master   // Push & Deploy as previously done
```

##### Provisioning Add-ons

```
heroku addons                          // List existing add-ons installed
heroku addons:create papertrail        // Provision an add-on
heroku addons:docs papertrail          // View supporting docs
heroku addons:open papertrail          // To see Add-on in action
```

##### One-off dyno

```
You can run a command, typically scripts and applications that are part of your app, in a one-off dyno using the
heroku run command. It can also be used to launch a REPL process attached to your local terminal for experimenting in
your app’s environment:

heroku run node        // Run node REPL
heroku run bash        // Run bash to open a shell on that dyno, you'll be able to navigate through files.

You most likely will be limited in running this since free accounts let you run only one dyno
```

##### Config Vars

```
Heroku lets you externalise configuration - storing data such as encryption keys or external resource addresses.
At runtime, config vars are exposed as environment variables to the application by reading the ".env" file.
In the top-level directory of your project there is already a .env file.

heroku config                // View existing configs, if any
heroku config:set TIMES=2    // Set a config on Heroku

https://devcenter.heroku.com/articles/config-vars
```

##### Provisioning a Database

```
The add-on marketplace has a large number of data stores, from Redis and MongoDB providers, to Postgres and MySQL.
Heroku has a free Postgres Starter Tier dev database for your app.
Once installed, DB url can be accessed from config with name DATABASE_URL
For local development, install Postgres locally

heroku addons:create heroku-postgresql:hobby-dev        // Adding the database to the app

heroku pg:info          // All PostgreSQL databases provisioned by app and identifying characteristics of each
watch heroku pg:info    // To continuously monitor the status of your database. pass through the unix watch command
heroku pg:psql          // To establish a session with your remote database
                        // Note: If you are unable to connect, check if you are on a private network with internal IP

Creating and inserting in a table
=> create table test_table (id integer, name text);
=> insert into test_table values (1, 'hello database');
=> \q

heroku pg:ps
heroku pg:kill 31912
heroku pg:kill --force 32670

https://devcenter.heroku.com/articles/heroku-postgresql#local-setup
http://postgresapp.com/
```



