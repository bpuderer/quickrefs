Command|Description
---|---
docker --version, docker version|
docker info|
docker build -t \<image> .|create Docker image and specify name
docker image ls|list images
docker image rm \<image id>|remove image
docker image rm $(docker image ls -a -q)|remove all images
docker run -p \<host port>:\<container port> \<image>|run container and publish container port to host port. -d option to run in detached/background mode
docker run -p \<host port>:\<container port> username/repository:tag|run from remote repository
docker container start \<container>|start stopped container
docker container stop \<container>|stop container
docker ps|list running containers. -a to show all
docker container ls|list running containers. -a to show all
docker container rm \<container>|remove container
docker container rm $(docker container ls -a -q)|remove all containers
docker logs <container>|return container logs. add -f to follow. --tail=\<# lines>
docker attach --sig-proxy=false <container>|attach to running container. set --sig-proxy=false so ^C does not stop container
docker tag \<image> \<username/repository:tag>|tag image
docker push \<username/repository:tag>|publish image


container- runtime instance of image  
image- executable package which includes everything needed to run  
registry - collection of repositories  
repository - collection of images  
Dockerfile - defines container config  

[Dockerfile](https://docs.docker.com/engine/reference/builder/)  
[Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/)  
[Get Started](https://docs.docker.com/get-started/)  
