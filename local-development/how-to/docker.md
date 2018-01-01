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
docker run -p 49160:8080 -d <your username>/node-web-app
```



