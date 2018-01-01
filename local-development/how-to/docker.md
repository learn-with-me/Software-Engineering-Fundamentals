# Docker

##### File .dockerignore

```
node_modules
npm-debug.log
```

##### Sample Dockerfile - Node

```
FROM node:carbon

# Create app directory
WORKDIR /usr/src/app

# Install app dependencies
COPY package*.json ./
RUN npm install

# Bundle app source
COPY . .

EXPOSE 8080
CMD [ "npm", "start" ]
```

##### Building image of your app

```
Make sure you have a Dockerfile present

$ docker build -t <repo_name/vendor_name>/<out_name>:<tag> <src_dir>      // -t is tagged release
$ docker build -t goel/twelve-factor:0.1 .
$ docker images                                                           // Verify the images built
```

##### Running the image

```
// -d runs the container in detached mode, leaving the container running in the background
// -p flag redirects a public port to a private port inside the container
// Here Docker mapped the 8080 port inside of the container to the port 49160 on your machine.

$ docker run -p 49160:8080 -d <repo_name/vendor_name>/<out_name>:<tag>
$ docker run -p 49160:8080 -d goel/twelve-factor:0.1
$ docker ps                                     # Print out container IDs
$ docker logs <container id>                    # Print app output
$ docker exec -it <container id> /bin/bash      # Enter the container
$ curl -i localhost:49160                       # call your app using curl
```

##### Resources

```
https://nodejs.org/en/docs/guides/nodejs-docker-webapp/
```



