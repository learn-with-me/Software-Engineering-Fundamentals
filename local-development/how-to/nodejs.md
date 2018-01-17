# Node.js Tricks

##### Create a simple server

```
var http = require('http');

http.createServer(function(request, response) {
  response.writeHead(200, {"Content-type": "text/plain"});
  response.end("Hello world!");
}).listen(8000);
```

##### Setting up express app

```
var express = require('express');
var app = express();
var engines = require('consolidate');

app.engine('html', engines.nunjucks);    // HTML templating engine
app.set('view engine', 'html');
app.set('views', __dirname + '/views');
app.use(express.bodyparser());            // binds post variables to req.body.xxx
app.use(app.router);                      // enables routing in express app

app.get('/', function(req, res) {
    // res.send('hello world');
    res.render('hello', {'name': 'Templates'});        // hello is the name of the template file
});

app.use(function(req, res) {
    res.sendStatus(404);
});

var server = app.listen(3000, function() {
    var port = server.address.port();
});
```

##### Handling environment variables

    If you have a single environment variable, you can fire the node process as
    $ KEY=value node index.js
    $ MONGO_URI=mongodb://localhost:27017/myNewDatabase node index.js

    In case of multiple variables, one of the ways is to add `dotenv` as a dependency. Follow the commands
    1. $ yarn add dotenv
    2. Move your environment variables in the .env file
    3. Execute this line before any other code:
            require('dotenv').config();
    4. Now finally execute your node process as usual
            $ node index.js

##### Proxy path to a CDN

    Intend to set custom path to an image request

    Express App
    1. Add `express-http-proxy` as dependency
        $ yarn add express-http-proxy
    2. Add the following code

    const proxy = require('express-http-proxy');
    const baseImageUrl = process.env.BASE_IMAGE_URL;

    const proxyBaseImageUrl = baseImageUrl
    ? proxy(baseImageUrl, {
        proxyReqPathResolver: function(req) {
          const newPath = baseImageUrl + req.path;
          console.log(newPath);
          return newPath;
        }
      })
    : express.static(path.join(__dirname, 'public/images'));

    const app = express();
    app.use('/images', proxyBaseImageUrl);

##### Libraries

```
express            - FE web framework
consolidate        - a wrapper for number of template engines for express
    nunjucks       - Requires installation if needed be used
mongodb            - MongoDB node.js driver (converts json to bson, opening sockets, managing connections, etc)
```



