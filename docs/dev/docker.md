# Docker Frequently Used Commands

## General

- `docker` - show commands & management commands
- `docker version` - show docker version
- `docker info` - show info like number of containers, etc

### Purging All Unused or Dangling Images, Containers, Volumes, and Networks
- Docker provides a single command that will clean up any resources — images, containers, volumes, and networks — that are dangling (not associated with a container):
    ```
    docker system prune
    ```
- To additionally remove any stopped containers and all unused images (not just dangling images), add the -a flag to the command:
    ```
    docker system prune -a
    ```

### Resolve potential IP Conflicts caused by Docker

!!! info ""
    Reference: [How To Change The Default Docker Subnet](https://support.zenoss.com/hc/en-us/articles/203582809-How-to-Change-the-Default-Docker-Subnet)

Docker uses the default 172.17.0.0/16 subnet for container networking. If this subnet is not available for docker in your environment (for example because your network already uses this subnet), you must configure Docker to use a different subnet.

## Working with Docker Images 

### List local images

- `docker images` - list all images
- `docker images -f dangling=true` - list all dangling images (`-f` for filter)

### Remove image(s)

- `docker image rm` - remove one or more images from local
- `docker image prune` - remove all unused (dangling) images

### Re-tag an image

```
docker image tag [image:tag(current)] [image:tag(new)]
```

### Build an image from current working directory

```
docker build -t [username/repo-name:tag] .
```

### Push an image to Docker Hub Repository

```
docker login
docker push [image]
```

## Working with Docker Container

### List containers

- `docker ps` - list running containers
- `docker ps -a` - list all containers, `-a` for all
- `docker ps -a -f status=exited` - list all exited containers, `-f` for filter

### Stop containers

- Stop a container
  ```
  docker container stop [ID]
  ```
- Stop all running containers
  ```
  docker stop $(docker ps -aq)
  ```


### Remove all exited containers

- Remove a exited container
  ```
  docker rm [ID]
  ```
- Remove all exited containers
  ```
  docker rm $(docker ps -a -f status=exited -q)
  ```
    - `-q` returns the ids of the containers


### Run a new container

```
docker run [OPTIONS] IMAGE [COMMAND] [ARG...]
```

- Create an run a container in foreground
  ```
  $ docker container run -it -p 80:80 --name nginx-server nginx
  ```
- Create an run a container in background
  ```
  $ docker container run -d -p 80:80 --name nginx-server nginx
  ```
- Start an ubuntu container interactively and destroy on exited
  ```
  docker container run --rm -it ubuntu
  ```

> WHAT `RUN` DID
> 
> - Looked for image called nginx in image cache
> - If not found in cache, it looks to the default image repo on Docker Hub
> - Pulled it down (latest version), stored in the image cache
> - Started it in a new container
> - We specified to take port 80- on the host and forward to port 80 on the container
> - We could do "$ docker container run --publish 8000:80 --detach nginx" to use port 8000


### Run the bash shell in a container interactively
```
docker exec -it [CONTAINER NAME] bash
```

### Get logs (Use name or ID)

```
docker container logs [NAME]
```

### List processes running in container

```
docker container top [NAME]
```

### View info on container

```
docker container inspect [NAME]
```

### Specific property (--format)

```
docker container inspect --format '{{ .NetworkSettings.IPAddress }}' [NAME]
```

### Performance stats (cpu, mem, network, disk, etc)

```
docker container stats [NAME]
```


---

Below To Be cleaned up

--- 




### Some sample container creation

NGINX:

```
$ docker container run -d -p 80:80 --name nginx nginx (-p 80:80 is optional as it runs on 80 by default)
```

APACHE:

```
$ docker container run -d -p 8080:80 --name apache httpd
```

MONGODB:

```
$ docker container run -d -p 27017:27017 --name mongo mongo
```

MYSQL:

```
$ docker container run -d -p 3306:3306 --name mysql --env MYSQL_ROOT_PASSWORD=123456 mysql
```

### Create new nginx container and bash into

```
$ docker container run -it --name [NAME] nginx bash
```

- i = interactive Keep STDIN open if not attached
- t = tty - Open prompt

**For Git Bash, use "winpty"**

```
$ winpty docker container run -it --name [NAME] nginx bash
```

### Access an already created container, start with -ai

```
$ docker container start -ai ubuntu
```

### Use exec to edit config, etc

```
$ docker container exec -it mysql bash
```

### Alpine is a very small Linux distro good for docker

```
$ docker container run -it alpine sh
```

(use sh because it does not include bash)
(alpine uses apk for its package manager - can install bash if you want)

## NETWORKING

### "bridge" or "docker0" is the default network

### Get port

```
$ docker container port [NAME]
```

### List networks

```
$ docker network ls
```

### Inspect network

```
$ docker network inspect [NETWORK_NAME]
("bridge" is default)
```

### Create network

```
$ docker network create [NETWORK_NAME]
```

### Create container on network

```
$ docker container run -d --name [NAME] --network [NETWORK_NAME] nginx
```

### Connect existing container to network

```
$ docker network connect [NETWORK_NAME] [CONTAINER_NAME]
```

### Disconnect container from network

```
$ docker network disconnect [NETWORK_NAME] [CONTAINER_NAME]
```

### Detach network from container

```
$ docker network disconnect
```


