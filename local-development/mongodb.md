# MongoDB

##### Starting the server and instantiating Database

```
1. You'll need three terminal instances
2. Terminal 1: Execute the following command to kick start your MongoDB server
    $ mongod
3. Terminal 2: Execute the following command and following sequence to setup the database
    $ mongo // opens up the mongo shell
    > show dbs // Display the list of available databases
    > use <database_name> // You can select existing database or create new with this command and set it to use
    > db // Execute to verify if the database you expected is in use
4. Terminal 3: This is where you run your node script. Examples below:
    Remember:
    1. For local you'll use localhost and 27017 is the default MongoDB port, feel free to change it.
    2. It is ideal to store the URI in environment variable

var MongoClient = require('mongodb').MongoClient;

MongoClient.connect("mongodb://localhost:27017/myNewDatabase", function(err, data) {
    if (err) {
        console.log('Cannot connect to MongoDB', err);
    } else {
        console.log('Connected to MongoDB');
    }
});
```



