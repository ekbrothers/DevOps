# Quicklinks
* [Docker Run Reference](https://docs.docker.com/engine/reference/run/)
* [DockerFile Reference](https://docs.docker.com/v17.09/engine/reference/builder/)
* [Docker CLI Cheat Sheet](https://devhints.io/docker)
* [Docker Cheat Sheet (GitHub)](https://github.com/wsargent/docker-cheat-sheet/blob/master/README.md)
* [Docker Getting Started](https://docs.docker.com/get-started/)

## Difference between Images, Dockerfiles, Docker containers
* A **Dockerfile** is a recipe for creating Docker images
* A **Docker image** gets built by running a Docker command (which uses that Dockerfile)
* A **Docker container** is a running instance of a Docker image

## Lab Notes
**Log in to Docker Hub via CLI**
<br>
`docker login`

**Pull Image from Hub**<br>
`docker pull IMAGE`

**List all images**<br>
`docker images`

**Run image**<br>
`docker run IMAGE`

**Show all running containers**<br>
`docker ps`

**Run image with interactive terminal (-it)**<br>
`docker run -it IMAGE`

**Remove exited container**<br>
`docker rm IMAGE ID`

**Remove more than one exited container (-f is filter)**<br>
`docker rm $(docker ps -a -q -f status=exited)`<br>
`docker container prune`

**run image that removes container after exit**<br>
`docker run --rm IMAGE`

**run image in detached mode (-d) with ports exposed (-P) and named a certain name (--name)**<br>
`docker run -d -P --name [NAME] [IMAGE]`

**view docker port of container**<br>
`docker port [CONTAINER]`

**specify custom port to which client will fwd connections**<br>
`docker run -p [port:port] [IMAGE]`

**push docker image to docker hub**<br>
`docker push namespace/IMAGE` 

**build image from dockerfile with tag (-t)**<br>
`docker build -t namespace/DIRECTORY`

**See container log**<br>
`docker container logs NAME`

docker build -t friendlyhello .  # Create image using this directory's Dockerfile
docker run -p 4000:80 friendlyhello  # Run "friendlyhello" mapping port 4000 to 80
docker run -d -p 4000:80 friendlyhello         # Same thing, but in detached mode
docker container ls                                # List all running containers
docker container ls -a             # List all containers, even those not running
docker container stop <hash>           # Gracefully stop the specified container
docker container kill <hash>         # Force shutdown of the specified container
docker container rm <hash>        # Remove specified container from this machine
docker container rm $(docker container ls -a -q)         # Remove all containers
docker image ls -a                             # List all images on this machine
docker image rm <image id>            # Remove specified image from this machine
docker image rm $(docker image ls -a -q)   # Remove all images from this machine
docker login             # Log in this CLI session using your Docker credentials
docker tag <image> username/repository:tag  # Tag <image> for upload to registry
docker push username/repository:tag            # Upload tagged image to registry
docker run username/repository:tag                   # Run image from a registry







