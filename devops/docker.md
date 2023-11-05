# Docker

## Overview

Docker is an open-source platform designed for automating the deployment, scaling, and management of applications within lightweight and stand-alone executable packages known as containers. Containers virtualize the operating system of the host, allowing an application to run in an isolated environment with its dependencies. Docker utilizes resource isolation features of the Linux kernel such as cgroups and namespace isolation to allow independent containers to run within a single Linux instance, avoiding the overhead of starting and maintaining virtual machines. It is imperative for users to peruse the official documentation for comprehensive understanding and effective utilization of Docker, along with any technology that is being assimilated into their workflow.

Here are crucial links for commencing your journey with Docker:

[Official Website](https://www.docker.com/)

[Docker Get Started Guide](https://docs.docker.com/get-started/overview/)

## Docker Architecture and Components

### Docker Engine
The Docker Engine encompasses the Docker daemon (`dockerd`), which is a persistent background process that manages the lifecycle of Docker containers. It facilitates the tasks of building, running, distributing, and orchestrating containers and interacts with other daemons for multi-node deployments. In-depth documentation is available at the [Docker Engine Documentation](https://docs.docker.com/engine/).

### Docker CLI
The Docker Command Line Interface (CLI) is the user's gateway to interact with Docker. It converts command-line inputs into API requests for the Docker daemon, enabling the creation, management, and orchestration of Docker containers, images, networks, and volumes. Documentation for the Docker CLI can be found at [Docker CLI Documentation](https://docs.docker.com/engine/reference/commandline/cli/).

### Docker Compose
Docker Compose is an orchestration tool for defining and running multi-container Docker applications. Utilizing a `YAML` configuration file, it streamlines the process of configuring application services, networks, and volumes. Compose enables the instantiation and operation of an application's services with a single command set. The comprehensive guide is provided in the [Docker Compose Documentation](https://docs.docker.com/compose/).

### Docker Hub
Docker Hub serves as a centralized registry service for container image management and dissemination. Comparable to a version control repository for Docker images, it facilitates both public and private image storage. Developers utilize Docker Hub for pushing and pulling images, providing a base for further image customization. Access Docker Hub at [Docker Hub](https://hub.docker.com/).


## Installation and Initial Configuration


### Installing Docker Engine and Docker Compose

The Docker Engine supports various Linux distributions, macOS, and Windows. The following commands illustrate the installation on Ubuntu. Refer to the [Docker Engine Installation Guide](https://docs.docker.com/engine/install/ubuntu/) for detailed instructions.

```bash
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

### Post-Installation Steps

To enable a non-root user to run Docker commands, add your user to the docker group. This step enhances the security and usability of Docker.

```bash
sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker
```


### Managing Docker

#### Checking Docker Status
To assess the state of the Docker daemon and to monitor Docker-related processes, you can use the following commands:

```bash
# Filter out Docker-related processes
ps -ef | grep docker

# Find the process ID for Docker daemon
pgrep docker

# Check the active status of the Docker service
sudo systemctl status docker
```

#### Starting Docker Service
To initiate the Docker daemon:

```bash
sudo systemctl start docker
```

#### Stopping Docker Service
To terminate the Docker daemon:

```bash
sudo systemctl stop docker
```

#### Displaying Docker System Information
To obtain detailed information about the Docker installation, including the number of containers and images, default configuration settings, and runtime metrics:

```bash
sudo docker info
```

#### Testing Docker Installation
To verify that Docker has been installed correctly and is functional, you can run the hello-world image which is a minimal Docker container:

```bash
sudo docker run hello-world
```

This command downloads a test image and runs it in a container. When the container runs, it prints an informational message and exits.


## Container Lifecycle Management

### Starting a New Container
To deploy a new container from an image, use `docker run`:

```bash
docker run [OPTIONS] IMAGE [COMMAND] [ARG...]
```

### Managing Containers
Commands to list, stop, start, and remove containers:

```bash
# List all containers
docker ps -a

# Stop a specific container
docker stop CONTAINER_ID

# Start a specific container
docker start CONTAINER_ID

# Remove a specific container
docker rm CONTAINER_ID
```

### Creating and Running a Container Example

```bash
sudo docker run -itd --name ubuntu-container ubuntu /bin/bash
```

Key options explained:
- -i (or --interactive): Keep STDIN open even if not attached.
- -t (or --tty): Allocate a pseudo-TTY, associating a terminal with the container.
- --name: Assign a name to the container for easier management.
- -d (or --detach): Run the container in the background.
- -p: Publish a container's port(s) to the host.
- -v: Bind mount a volume.


#### Attaching to a Container
To attach your terminal to a running container:

```bash
# List all containers to get the CONTAINER ID
sudo docker ps -a

# Attach to the container
sudo docker attach CONTAINER_ID
```

Note: If you created the container without -d, you're automatically attached to it.

To detach from the container without stopping it, use the CTRL-p CTRL-q sequence.
 
#### Starting a Stopped Container
To start a previously stopped container:

```bash
# Start the container by its name
sudo docker start ubuntu-container

# Verify the container is running
sudo docker ps -a
```

#### Executing Commands Inside a Container
To execute a command inside a running container:

```bash
sudo docker exec -it ubuntu-container COMMAND
```

#### Stopping a Running Container
To stop a running container:

```bash
sudo docker stop ubuntu-container
# Verify the container has stopped
sudo docker ps -a
```


#### Removing a Container
To remove a container:

```bash
# Remove a stopped container by ID or name
sudo docker rm CONTAINER_ID_OR_NAME

# Forcefully remove a running container
sudo docker rm --force CONTAINER_ID_OR_NAME
```



## Managing Images

### Searching for Images
To list all downloaded images on your local system:

```bash
sudo docker images
```

To search for images in a registry, use the docker search command followed by the image name:

```bash
sudo docker search IMAGE_NAME
```

For example, to search for official Ubuntu, MySQL, and Nginx images in Docker Hub:

```bash
sudo docker search ubuntu  
sudo docker search mysql  
sudo docker search nginx  
```
Access to shared community images is available at [Docker Hub](https://hub.docker.com/ ).

### Dowloading Images
To download an image from a registry such as Docker Hub:

```bash
docker pull IMAGE_NAME:TAG
```

For example, to pull the latest Ubuntu image:

```bash
docker pull ubuntu:latest
```
Inspecting images provides detailed information about the image layers, configuration, and other metadata:

```bash
sudo docker image inspect `IMAGE_ID`
```
For instance, to inspect the Ubuntu image:

```bash			
sudo docker image inspect ubuntu
```

Removing images is done using the rmi command:

```bash
docker rmi IMAGE_ID_OR_NAME
```



## Building Images

To build an image from a Dockerfile:

```bash
docker build -t IMAGE_NAME:TAG PATH_TO_DOCKERFILE
```

### Creating a Dockerfile

Tip: Only one Dockerfile should be present per directory.

Contents of the Dockerfile:

- FROM: Must be the first command - specifies the base image from which to build.
- RUN: Command that will be executed during the build.
- ENV: Set environment variables.
- CMD: Should be the last command - specifies the command to run when the container starts.

Example Dockerfile for a network service:

```bash
# Use an editor to create a Dockerfile
$ nano Dockerfile

# Content of the Dockerfile
FROM ubuntu
LABEL maintainer="ed"
RUN apt-get update -y && apt-get install -y net-tools iputils-ping
RUN mkdir -p /test  
RUN useradd appuser   
RUN usermod -aG sudo appuser  
USER appuser  
```

Build the Docker image with the following command, specifying the image name, tag, and location of the Dockerfile (use . for the current directory):
```bash
sudo docker build -t my_image_name:version -f Dockerfile .
````
For example:

```bash
sudo docker build -t ubuntu:2903 -f Dockerfile .
# Check the built image
sudo docker images
# Run a container from the new image
sudo docker run -it ubuntu:2903 /bin/bash
```

### Creating a New Image from a Container
To create a new image from a container's changes:

```bash
# List all containers
sudo docker ps -a
# Commit changes in a container to an image
sudo docker commit CONTAINER_ID my_new_image
# Check the new image
sudo docker images
```

To exit the container without stopping it, use exit or CTRL-p CTRL-q.

### Pushing an Image to Docker Hub
Before pushing an image, make sure to tag it with your Docker Hub username and log in to Docker Hub.
docker push 

```bash
# Tag your image
docker tag my_image:my_tag myusername/my_image:my_tag
# Push your image
docker push myusername/my_image:my_tag
```

### Inspecting Docker's Storage Directories
To look at Docker's container and image storage directories:

```bash
# List the contents of the containers directory
sudo ls /var/lib/docker/containers -l

# List the contents of the image directory
sudo ls /var/lib/docker/image -l
```



## Docker Compose

Docker Compose is a tool designed for defining and orchestrating multi-container Docker applications. With Compose, you use a YAML file (`docker-compose.yml`) to configure your application’s services, and then, with a single command, you create and start all the services from your configuration.

### Compose File Structure

The `docker-compose.yml` file is a YAML file defining services, networks, and volumes. A service definition contains configuration that is applied to each container started for that service, much like passing command-line parameters to `docker run`. Likewise, network and volume definitions are analogous to `docker network create` and `docker volume create`.

Here is a simple example of a `docker-compose.yml` file:

```yaml
version: '3.8' # specifies the Docker Compose file version
services:
  web:
    image: nginx:alpine
    ports:
      - "80:80"
    volumes:
      - ./html:/usr/share/nginx/html
  db:
    image: postgres:latest
    environment:
      POSTGRES_PASSWORD: mysecretpassword
networks:
  mynet:
    driver: bridge
volumes:
  db-data:
```

### Basic Commands
To build and start your application from your project directory (where the docker-compose.yml file is located):

```bash
docker-compose up
```

To stop and remove containers, networks created by up:

```bash
docker-compose down
```

To rebuild services after a change:

```bash
docker-compose up --build
```

To start services in detached mode (run containers in the background):

```bash
docker-compose up -d
```

To stop services without removing them:

```bash
docker-compose stop
```

To restart services:

```bash
docker-compose restart
```

To list containers:

```bash
docker-compose ps
```

To view output from containers:

```bash
docker-compose logs
```

To execute a command in a service:

```bash
docker-compose exec SERVICE_NAME COMMAND
```

For example, to open a bash shell in the 'web' service container:

```bash
docker-compose exec web /bin/bash
```

To run a one-off command on a service:

```bash
docker-compose run --rm SERVICE_NAME COMMAND
```

To remove stopped service containers:

```bash
docker-compose rm
To pull all images without starting containers:

```bash
docker-compose pull
```


## Networking

Docker has various networking options to link containers, expose ports, and even create custom bridges.

### Basic Networking Commands

```bash
docker network ls
docker network create NETWORK_NAME
docker network rm NETWORK_NAME
```

## Storage and Volumes

Docker allows mounting volumes for persistent storage and data sharing between containers.

```bash
docker volume create VOLUME_NAME
docker volume ls
docker volume rm VOLUME_NAME
```

## Best Practices

- Use `.dockerignore` files to exclude files that are not necessary for building a Docker image.
- Always specify a tag when pulling images. E.g., `docker pull nginx:1.19` instead of `docker pull nginx`.
- Use multi-stage builds for minimizing image size.
- Use official base images whenever possible.
- Regularly update images for security patches.
- 
