# Go in Heroku

##### Setup verification

```
go version
```

##### Configuration

    Procfile
    web: go-getting-started

    vendor.json
    Heroku recognizes a Go app by this file's existence in the vendor directory located in application’s root directory.
    The `vendor/vendor.json` file is used by `govendor` and specifies both the dependencies that are vendored with your
    application and the build configuration Heroku should use to compile the application.

    os.Getenv("PORT")

##### Dependency Management

```
https://github.com/kardianos/govendor
https://devcenter.heroku.com/articles/go-dependencies-via-godep
https://devcenter.heroku.com/articles/go-dependencies-via-gb
```

##### Web Frameworks

```
https://github.com/codegangsta/negroni
https://github.com/gin-gonic/gin
http://golang.org/pkg/net/http/
```

##### Database

```
heroku addons:create heroku-postgresql:hobby-dev

Install Postgresql Go library
govendor fetch github.com/lib/pq
```



