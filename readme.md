# Setting up docker for an app

`docker --version` Docker version 17.09.0-ce, build afdb6d4

`docker run hello-world` Test environment is set up

`Dockerfile` Defines what will happen in the environment inside the container

`requirements.txt` Contains required packages

`docker build -t <imagename> .` Create the Docker image

`docker image ls` Lists all the Docker images

`docker run -p 4000:80 <imagename>` Runs the app, mapping port 4000 to containers port 80

`docker run -d -p 4000:80 <imagename>` Runs app in detached mode

`docker container ls` Lists container IDs

`docker container stop <containerID>` Stop specified container

### Upload image to the cloud

`docker login` Login to Docker cloud

`docker tag <imagename> <username>/<repository>:<tag>` Associate a local image with a repository on the cloud

`docker push <username>/<repository>:<tag>` Upload tagged image to repository

`docker run -p 4000:80 <username>/<repository>:<tag>` Run Docker image from the cloud

### Docker services

`docker-compose.yml` Defines how Docker containers should behave in production

`docker stack deploy -c docker-compose.yml <appname>` Deploy and update the app with scaling

`docker stack rm <appname>` Take down the app

`docker service ls` Lists the services

`docker service ps <appname>` List all tasks for that service

`docker service ps <serviceid>` Lists all the containers in that service

`docker inspect --format='{{.Status.ContainerStatus.ContainerID}}' <taskid>` Returns the ID of its container

`docker inspect --format="{{index .Config.Labels \"com.docker.swarm.task.id\"}}" <containerid>` Returns the ID of its task

`docker container ls -q` Lists all the container IDs

### Swarms

Swarm - group of machines that are running Docker and joined in a cluster. Dock commands are executed on a cluster by a swarm manager

`docker swarm init` Enable swarm mode and make current machine swarm manager

`docker swarm join` Join the swarm as workers

`docker-machine create --driver virtualbox <vmName>` Using docker-machine to make a vm

`docker-machine ls` List the vm's and get their IP addresses

Send commands to vm's using `docker-machine ssh`

`docker-machine ssh <vmName> "docker swarm init --advertise-addr <vm IP>"` Initialise swarm in vm

`docker node ls` List nodes in the swarm

`docker swarm leave` Leave the swarm

`docker-machine env <vmName>` Configures shell to talk to the Docker daemon on the vm

`eval $(docker-machine env <vmName>)` Configure shell to talk to vm

`eval $(docker-machine env -u)` Disconnect shell from docker-machine

`docker-machine start <vmName>` Start a vm thats stopped
