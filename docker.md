Command|Description
---|---
docker --version, docker version|
docker info|
docker build -t \<name>:\<optional tag> \<path>|create Docker image from Dockerfile and name
docker image ls|list images
docker image rm \<image>|remove image
docker image rm $(docker image ls -a -q)|remove all images
docker run -p \<host port>:\<container port> \<image>|run container and publish container port to host port. -d option to run in detached/background mode
docker run -p \<host port>:\<container port> username/repository:tag|run from remote repository
docker container start \<container>|start stopped container
docker container stop \<container>|stop container
docker ps|list running containers. -a to show all
docker container ls|list running containers. -a to show all
docker container inspect \<container>|detailed info of container
docker container rm \<container>|remove container
docker container rm $(docker container ls -a -q)|remove all containers
docker logs <container>|return container logs. add -f to follow. --tail=\<# lines>
docker attach --sig-proxy=false <container>|attach to running container. set --sig-proxy=false so ^C does not stop container
docker login|login to hub.docker.com
docker tag \<image> \<username>/\<repository>:\<tag>|tag image
docker push \<username>/\<repository>:\<tag>|publish image to registry


Command|Description
---|---
docker swarm init|initialize a swarm, targeted engine becomes a manager
docker node ls|run on manager, list nodes in swarm
docker stack deploy -c \<compose yaml> \<stack>|run on manager, deploy new or update existing stack on swarm
docker stack ls|list stacks
docker stack ps \<stack>|run on manager, list tasks in the stack
docker service ls|run on manager, list services running in swarm
docker service inspect \<service>|detailed info of service
docker service ps \<service>|run on manager, list tasks for service
docker stack rm \<stack>|run on manager, remove stack from swarm
docker swarm leave|remove node from swarm. only use --force on manager if single node swarm
docker-machine create --driver virtualbox \<machine>|create VM
docker-machine ssh \<machine> "\<command>"|send command to machine
docker-machine ssh \<machine> "docker swarm init --advertise-addr \<machine ip>"|instruct machine to become swarm manager. will include command to send to other machines to join swarm
docker-machine env \<machine>|get commands to configure local shell to talk to machine rather than using docker-machine ssh
docker-machine ls|check status of machines
docker-machine scp \<file> \<machine>:~|scp file to machine (Compose yaml to manager to run docker stack deploy)
docker-machine stop $(docker-machine ls -q)|stop all running VMs
docker-machine rm $(docker-machine ls -q)|delete all VMs and images
docker node demote \<node>|demote manager to worker


container- runtime instance of image  
image - executable package which includes everything needed to run  
registry - collection of repositories  
repository - collection of images  
Dockerfile - defines container config  
Compose file - YAML that defines services, networks, volumes. ./docker-compose.yml  
service - only runs one image. parts of app  
task - single container running in a service  
swarm - cluster of machines running Docker  
node - Docker machine in swarm  
swarm manager - manages swarm based on Compose file. only swarm manager executes docker commands  
worker - provide capacity.  manager authenticates workers to join swarm  
stack - group of interrelated services that share dependencies, and can be orchestrated and scaled together  


[Get Started](https://docs.docker.com/get-started/)  
[Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/)  
[Docker Machine CLI](https://docs.docker.com/machine/reference/)  
[Dockerfile](https://docs.docker.com/engine/reference/builder/)  
[Compose file](https://docs.docker.com/compose/compose-file/)  
