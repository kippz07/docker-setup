# Setting up docker for an app

`docker --version` Docker version 17.09.0-ce, build afdb6d4

`docker run hello-world` Test environment is set up

`Dockerfile` Defines what will happen in the environment inside the container

`requirements.txt` Contains required packages

`docker build -t [imagename] .` Create the Docker image

`docker image ls` Lists all the Docker images

`docker run -p 4000:80 [imagename]` Runs the app, mapping port 4000 to containers port 80

`docker run -d -p 4000:80 [imagename]` Runs app in detached mode

`docker container ls` Lists container IDs

`docker container stop [containerID]` Stop specified container

### Upload image to the cloud

`docker login` Login to Docker cloud

`docker tag [imagename] [username]/[repository]:[tag]` Associate a local image with a repository on the cloud

`docker push [username]/[repository]:[tag]` Upload tagged image to repository

`docker run -p 4000:80 [username]/[repository]:[tag]` Run Docker image from the cloud

### Docker services

`docker-compose.yml` Defines how Docker containers should behave in production

`docker swarm init`

`docker stack deploy -c docker-compose.yml [appname]` Deploy the app with a name

`docker service ls` Lists the services

`docker service ps [serviceid]` Lists all the containers in that service

`docker inspect --format='{{.Status.ContainerStatus.ContainerID}}' [taskid]` Returns the ID of its container

`docker inspect --format="{{index .Config.Labels \"com.docker.swarm.task.id\"}}" [containerid]` Returns the ID of its task

`docker container ls -q` Lists all the container IDs
