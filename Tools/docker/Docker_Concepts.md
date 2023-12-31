> _**Docker**_ - platform that encapsulates application into containers, ensures that they work uniformly across different computing environment.

> _**Container**_ - lightweight, standalone, executable package that includes everything needed to run a piece of software (code, runtime, libs, env vars, config files)

* Containers are isolated from each other and handle their own software, but they can communicate with each other through well-defined channels

* Docker containers are **stateless**: any changes done inside a container will not be saved when the container is killed and started again. -> easy to restore initial state.

* Docker needs _**Docker Image**_ to act as an artifact to build up containers.

* Container has layers of images
    * Mostly **Linux Base** Image (since it has small footprint)
    * Application Image stays on top
    * Allow docker to run **multiple version** of an application at the same time (build on top of lower layer)

Ex: to run a container of mysql image
```pwsh
docker pull mysql:<specified tag>
docker run mysql
```

## Docker Containers vs VMs
![Docker Containers vs VMs](/Images/docker-containerized-and-vm-transparent-bg.png)

* A VM is a full abstraction of an entire OS, running on **virtualized hardware**.

* Docker Container shares the host system's kernel with other containers, and runs a discrete process in user space.
    * These factors make Docker Container less resource-demanding.

## Port Binding
![Docker port binding](/Images/docker-port-binding.png)

* There are multiple containers that run on the host machine.
    * But there are only certain ports available.

* Containers can listen on the same port, as long as they are binded to different port of host machine.

```pwsh
docker run -p 3306:3306 --name mtu_mysql mysql
```

## Docker Network

> _**Docker Networking**_ - a system by which Docker Containers communicate with each other and wit external systems.

![Docker networking](/Images/docker-networking.png)

* Containers can communicate with each other on the same Docker host or across different Docker hosts

* There can be different networks for different applications, providing network-level isolation for containers.

* Docker networking allows to map ports from the Docker host to containers, make it possible to expose container services to the outside.

* Docker networking provides built-in service discovery, allowing containers to refer to each other by name instead of IP address.

Ex:
```pwsh
# Create a network
docker network create my_network

# Run a container on the network
docker run --network=my_network -d --name my_container my_image
```

## Docker Compose
> tool for defining and running **multiple containers** at the same time with a single command.

```yaml
# an sample yaml file
version: '3'
services:
  mongodb:
    image: mongo
    ports:
      - 27017:27017
    environment:
      - MONGO_INITDB_ROOT_USERNAME=admin
      - MONGO_INITDB_ROOT_PASSWORD=password
  mongo-express:
    image: mongo-express
    restart: always # fixes MongoNetworkError when mongodb is not ready when mongo-express starts
    ports:
      - 8080:8081
    environment:
      - ME_CONFIG_MONGODB_ADMINUSERNAME=admin
      - ME_CONFIG_MONGODB_ADMINPASSWORD=password
      - ME_CONFIG_MONGODB_SERVER=mongodb
```

Then run the yaml file by using command
```shell
docker-compose -f <path-to-file> up

# to shut it down
docker-compose -f <path-to-file> down
```

_(when running up the docker compose, a network will be created, which encloses all containers)_

## Docker Volume
> Mechanism for persisting data generated by and used by Docker containers. 

* Docker Volume are managed by Docker and can survive container restarts/shutdowns.

### Use cases for Docker Volume
* User wants to store data generated by containers that should persist after a container is stopped or deleted.

* User wants to share data between containers.

![Docker Volume share data](/Images/docker-volume.png)

* User wants to store data in a external location, outside of the container's filesystem
    * For performance boost
    * For backup/recovery

### Types of Docker Volume
* **Persistent Volumes**: These are the normal type of Docker Volumes that persist data even after the container is stopped or deleted.

```pwsh
docker run -v volume_name:</path/in/container> my_image
```

* **Bind Mounts**: These can be stored anywhere on the host system. They may even be important system files or directories. Bind mounts have limited functionality compared to volumes.

```pwsh
docker run -v </path/on/host>:</path/in/container> my_image
```

* **tmpfs Mounts**: These are stored in the host system's memory only, and are never written to the host system's filesystem.

```pwsh
docker run --tmpfs </path/in/container> my_image
```

## Build Docker Image

```dockerfile
# Sample Dockerfile

FROM node:13-alpine

ENV MONGO_DB_USERNAME=admin \
    MONGO_DB_PWD=password

RUN mkdir -p /home/app

COPY ./app /home/app

# set default dir so that next commands executes in /home/app dir
WORKDIR /home/app

# will execute npm install in /home/app because of WORKDIR
RUN npm install

# no need for /home/app/server.js because of WORKDIR
CMD ["node", "server.js"]
```

```pwsh
docker build -t my_image_name:my_tag <path-to-dockerfile>
```