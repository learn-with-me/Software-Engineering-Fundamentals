# Node.js in Heroku

Heroku recognizes an app as Node.js app by the existence of a `package.json` file in the root directory. Heroku reads this file and installs the appropriate node version together with the dependencies using the npm install command.

##### Setup Verification

```
node -v
npm -v
git --version

It is good to define the environment you want your app to run in package.json
Config vars can be accessed by process.env.TIMES
```

##### Database

```
To access the free tier database, add "pg" as a dependency in package.json
"pg": "6.x"

var pg = require('pg');

app.get('/db', function (request, response) {
  pg.connect(process.env.DATABASE_URL, function(err, client, done) {
    client.query('SELECT * FROM test_table', function(err, result) {
      done();
      if (err)
       { console.error(err); response.send("Error " + err); }
      else
       { response.render('pages/db', {results: result.rows} ); }
    });
  });
});
```



