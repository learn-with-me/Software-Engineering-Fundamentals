# MySQL

##### Installation

```
$ sudo apt-get install mysql-server        // Download, install and start the server
$ sudo mysql_secure_installation           // Secure MySQL using the mysql_secure_installation utility
```

##### Optimize for 2GB server

```
$ sudo nano /etc/mysql/my.cnf            // Open the MySQL configuration file for editing
• Comment out all lines beginning with key_buffer. This is a deprecated setting and we’ll use the correct option.
• Edit following values
    [mysqld]
    max_allowed_packet = 1M
    thread_stack = 128K
    max_connections = 75
• Add the following lines to the end of my.cnf
    table_open_cache = 32M
    key_buffer_size = 32M

$ sudo service mysql restart            // Restart MySQL server
```

##### Commands

```
$ mysql -u root -p                // Log in using the MySQL root password
$ CREATE DATABASE exampleDB;      // Create a database

Create a new user in MySQL and then grant that user permission to access the new database
$ GRANT ALL ON exampleDB.* TO 'example_user' IDENTIFIED BY 'password';

$ FLUSH PRIVILEGES;                // Tell MySQL to reload the grant tables
$ quit                             // Exit MySQL console

Import a database

```



