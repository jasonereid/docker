# Docker
Notes about docker

Docker containers are not meant to be peristant, like a PC OS. They are meant to run a job, function, computation, etc., and when that task is done, they are supposed to stop (exits). The container only runs as long as the task is running. Running "docker run ubuntu" will result in a container spinning up and then exiting immediately, because there is no task. Running "docker run ubuntu sleep 5" will start a container for 5 seconds, because it has a task (sleep) appended to it.

In any Docker command, if you want to specify a particular container, you can just provide the first 5 characters of the container ID (as long as they are different from other containers) rather than the entire ID - i.e. a043d rather than a043d945kdfksko59er99043434kifkf49040.

Official Docker images: https://hub.docker.com/search?q=&type=image&image_filter=official

Images can be base operating systems, like Ubuntu, or they can operate as webservers (NGINX), or provide other functions like data structure servers or programming languages (Python, node, etc). Commond images include ubuntu, alpine, redis, nginx, centos, mongo.

Docker images are downloaded to the working directory. 

## The Docker Run Command

Basic command format:

        docker run <OPTIONS> <IMAGE_NAME>
        
        docker run -d --name mynew-sql-db -e MYSQL_ROOT_PASSWORD=password123! -p 3306:500 mysql

docker run creates and runs a container with the image and options your specify. If the iamge is not located locally, docker will automatically pull down the image from the dockerhub or your specified repo. 

Options for the docker run command:

--name - this allows you to name the container

-d - this makes the container run detached in the background. You can attach to it later to run commands on it.

-e - this allows you to run environmental variables. You need to specify a password for databases, pass along variables for web apps, etc.

-i - makes the container interactive so you can run commands

-t - opens up a terminal on the container - combine this with i to make -ti and you can directly run commands after the container starts

--network - specify the network / subnet to attach the container to

-v - allows you to bind a volume to your container so you can use an external (persistent) volume rather than a volume inside the container that will die with the container

-p - allows you to define and bind ports -p 5000:8081 binds external (host machine) port 5000 to container port 8081




## Other Docker Commands

docker ps - lists all running containers, use the -a option to see all containers regardless of whether they are running or not

docker stop <NAME_OF_CONTAINER> - stops container from running

docker rm <NAME_OF_CONTAINER> - removes a container (delete)

docker images - list of availible (local) images and their sizes
    
docker pull <IMAGE_NAME> - pulls down a container image to local so you don't have to download it later when you run it

docker exec <CONTAINER_NAME> <COMMAND> - executes a command on a running container. Example below runs the tail command to get the last lines of a txt file called "file.txt"
    
        docker exec my_ubuntu_01 tail /home/file.txt

docker run -it <IMAGE_NAME> bash - runs a container and gives you TTY, so you can operate bash inside the container.
    
docker version - displays Docker engine version running on host
    
docker images are stored in the /var/lib/docker/ folder
    
# Dockerfiles
    
Dockerfiles are built from a set of instructions telling the host how and where to install the files, what applications to run, and what ports to map. It follows a simple setup:
    
    FROM - this sets the image to base the container on
    RUN - 
    COPY
    EXPOSE
    WORKDIR
    ENTRYPOINT
    
    
To build an image from a Dockerfile, simply run a command on the directory containing the Dockerfile:
    
    docker build <DIRECTORY_DOCKERFILE>
    
