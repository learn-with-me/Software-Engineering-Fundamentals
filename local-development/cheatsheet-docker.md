# Docker Cheatsheet

##### Build

```
> docker build -t myapp:1.0                    // Build an image from Dockerfile in the current directory with a tag
> docker images                                // List all images locally stored with Docker engine
> docker rmi alpine:3.4                        // Delete an image from local image store
```

##### Ship

```
> docker pull alpine:3.4                        // Pull an image from a registry
> docker tag alpine:3.4 myrepo/myalpine:3.4     // Retag a local image with a new image name and tag
> docker login my.registry.com:8000             // Log into a registry (Docker Hub by default)
> docker push myrepo/myalpine:3.4               // Push an image to a registry
```

##### Run

```
> docker run                            // 
> docker start web                      // Start a container
> docker stop web                       // Stop a running container through SIGTERM
> docker kill web                       // Stop a running container through SIGKILL
> docker network ls                     // List the networks
> docker network create --subnet 10.1.0.0/24 --gateway 10.1.0.1 -d overlay mynet    // Create an overlay network
> docker ps                             // List the running containers
> docker rm -f $(docker ps -aq)         // Delete all running and stopped containers
> docker exec -it web bash              // Create a new bash process inside the container and connect it to the terminal
> docker logs --tail 100 web            // Print the last 100 lines of a container's logs
```

Docker Machine

```
> docker-machine create --driver=virtualbox myhost
```



