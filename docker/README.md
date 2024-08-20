# Docker documentation
 
# Table of contents  
1. [Docker Introduction](#introduction)
    1. [What is docker](#what-is-docker)
    2. [How to install docker](#how-to-install-docker)
    3. [Docker architecture](#docker-architecture)
2. [Docker File](#docker-file)
    1. [Introduction to docker file](#docker-file)
    2. [Docker file cheat sheet](Docker-file-cheat-sheet)
3. [Docker Image](#docker-image)  
    1. [Introduction to docker Image](#docker-image)
    2. [Image cheat sheet](#image-cheat-sheet)
4. [Docker container](#docker-container)
    1. [Introduction to docker container](#docker-container)
    2. [Container cheat sheet](#container-cheat-sheet)
5. [Docker networking](#docker-networking)
    1. [Different Types of Docker Network](#Different-Types-of-Docker-Network)
    2. [Networking cheat sheet](#Networking-cheat-sheet)
6. [Docker compose](#docker-compose)     
6. [Some miss conception about docker](#docker-misconception)
7. [Best practices](#best-practices)

# Introduction

### Docker architecture 
#### It have five part:
**Registry:** Its host public and official images. \
**Image:** Bluprint for run container. \
**Container:** Instance on Image. After run image we get container. \
**Daemon:** Its a service that run on host OS and manage docker image and container creation, run and monitoring. \
**Client:** Talk to daemon via API. 

![architecture](https://user-images.githubusercontent.com/14360563/217986211-f6c0e233-f845-439c-94d0-dd67180df36c.svg)


### Docker general command
| Image Command | Command description | 
| --------------- | --------------- |
|```docker info```|Display full information|
|```docker login -u <username>```|Login into Docker| 
|```docker push <username>/<image_name>```|Publish an image to Docker Hub|
|```docker system df```|docker daemon disk space usage| 
|```docker system prune -af```|Remove images, networks, containers, and volumes|
|```docker stats```|Resource usage by Docker containers| 
|```docker rmi <image_name>```|Delete an Image| 

### Common tag use by Docker
| Tag name | Tag meaning | 
| --------------- | --------------- |
|```-d```|detouched mode / backgound run|
|```-p```|port mapping| 
|```-it```|Interactive mode| 
|```-t```|for set tag name|
|```-f```|force|


### Image cheat sheet
| Image Command | Command description | 
| --------------- | --------------- |
|```docker image ls```|List of all local image |
|```docker build -t <image_name> .```|Build an image from a Dockerfile| 
|```docker image history```|Show the history of an image|
|```docker image inspect```|detailed information of images| 
|```docker image push```|Push image to registry|
|```docker image prune```| Remove all unused images | 
|```docker rmi <image_name>```|Delete an Image| 


### Container cheat sheet
| Container Command | Command description | 
| --------------- | --------------- |
|```docker ps```|Running containers list |
|```docker ps -a```|see both running and non-running|
|```docker exec -it <container name> /bin/sh```| SSH access inside container| 
|```docker create <image_name>```| Connect a container to a network | 
|```docker rename [container] [new-name]```| Connect a container to a network|
|```docker run -p <host_port>:<c_port> <image_name>```|Run container with port|
|```docker run -d <image_name>```|Run a container in the background| 
|```docker inspect <container_name/ id> ```|To inspect a running container|
|```docker start or stop <container_name/id>```|Start or stop an existing container|  
|```docker restart <container name>```|Restart a container| 
|```docker rm <container name>```| Remove a stopped container| 

## Docker networking
New network Example: ```docker network create --driver <driver-name> <network name>``` \
Connect a Docker Container to a Network example: ```docker network connect <network_id or n_name> <container_id or c_name>``` 

#### Different Types of Docker Network: \
**bridge(Default)**: The default network driver. If you don’t specify a driver, this is the type of network you are creating. Bridge networks are usually used when your applications run in standalone containers that need to communicate.\
**host**: For standalone containers, remove network isolation between the container and the Docker host, and use the host’s networking directly. \
**overlay**:  Overlay networks connect multiple Docker daemons together and enable swarm services to communicate with each other. \
**ipvlan**:  IPvlan networks give users total control over both IPv4 and IPv6 addressing. \
**macvlan** : Macvlan networks allow us to assign a MAC address to a container.\
**none**: This one used for disable all networking \
**Also we can make other network by using third party plugin

### Networking cheat sheet
| Networking Command | Networking Description | 
| --------------- | --------------- |
|```docker network ls``` | List networks |
|```docker network create``` | Create a network | 
|```docker network connect [network] [container]``` |Connect a container to a network| 
|```docker network disconnect [network] [container]``` |disconnect a container to a network|
|```docker network disconnect```|Dic connect docker network|
|```docker network inspect [network]```|See network info details|
|```docker network prune``` |Remove all unused networks| 
|```docker network rm [network]``` |Remove one or more networks|  


## Docker Volumes

### Introduction to Docker Volumes
Docker volumes are directories on the host filesystem that persist even after the container exits. They are a way to share data between a container and the host or between multiple containers.

### Volumes Cheat Sheet
| Volume Command | Command description | 
| --------------- | --------------- |
|`docker volume ls`|List all volumes|
|`docker volume create <volume_name>`|Create a Docker volume| 
|`docker volume inspect <volume_name>`|Get detailed information about a volume|
|`docker run -v <volume_name>:<container_path> <image_name>`|Attach a volume to a container|
|`docker volume prune`|Remove all unused volumes| 
|`docker volume rm <volume_name>`|Remove a specific volume| 

# Docker Compose 

Docker Compose is a tool for defining and running multi-container Docker applications. It uses YAML files to configure the application's services.

Below is a rundown of the common Docker Compose commands also shown with their corresponding descriptions in a tabular form:

| Docker Compose Commands | Description |
| --- | --- |
| `docker-compose up` | Build, create, start, and attach to containers for a service |
| `docker-compose down` | Stop and remove containers, networks, images, and volumes |
| `docker-compose build` | Build or rebuild services |
| `docker-compose ps` | List containers |
| `docker-compose start` | Start services |
| `docker-compose stop` | Stop services |
| `docker-compose restart` | Restart services |
| `docker-compose rm` | Remove stopped containers |
| `docker-compose logs` | View output from containers |
| `docker-compose pull` | Pull service images |
| `docker-compose exec` | Execute a command in a running container |

An example Docker Compose file usually consists of the following configuration:

```yaml
version: '3'
services:
    web:
        image: nginx:alpine
        ports:
            - "80:80"
    database:
        image: postgres
        volumes:
            - db_data:/var/lib/postgresql/data
volumes:
    db_data:
```
In the above example, we define two services, `web` and `database`. The `web` service uses the `nginx:alpine` image and maps port 80 on the host to port 80 on the container. The `database` service uses the `postgres` image and mounts the named volume `db_data` at the path `/var/lib/postgresql/data`.

Please note that Docker Compose is suited for development and testing environments, and for simpler production deployments. If you need to deploy in production, using `docker swarm` or a Kubernetes-based platform may be more suitable.
