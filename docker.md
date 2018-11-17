Command|Description
---|---
docker --version|
docker info|
docker build -t <image> .|create Docker image and specify name
docker image ls|list images
docker image rm <image id>|remove image
docker image rm $(docker image ls -a -q)|remove all images
docker run -p <host port>:<container port> <image>|run container and publish container port to host port. -d option to run in detached/background mode
docker container stop <container id>|stop container
docker ps|list running containers. -a to show all
docker container ls|list actively running containers. -a to show all
docker container rm <container id>|remove container
docker container rm $(docker container ls -a -q)|remove all containers
docker tag image username/repository:tag|tag image
docker push username/repository:tag|publish image
docker run -p <host port>:<container port> username/repository:tag|run from remote repository


container- runtime instance of image
image- executable package which includes everything needed to run
registry - collection of repositories
repository - collection of images
Dockerfile - defines container config
