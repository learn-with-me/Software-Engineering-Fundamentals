# Node.js Tricks

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



