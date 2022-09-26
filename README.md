# Docker
Notes about docker

Docker containers are not meant to be peristant, like a PC OS. They are meant to run a job, function, computation, etc., and when that task is done, they are supposed to stop (exits). The container only runs as long as the task is running. Running "docker run ubuntu" will result in a container spinning up and then exiting immediately, because there is no task. Running "docker run ubuntu sleep 5" will start a container for 5 seconds, because it has a task (sleep) appended to it.

In any Docker command, if you want to specify a particular container, you can just provide the first 5 characters of the container ID (as long as they are different from other containers) rather than the entire ID - i.e. a043d rather than a043d945kdfksko59er99043434kifkf49040.

Official Docker images: https://hub.docker.com/search?q=&type=image&image_filter=official

Images can be base operating systems, like Ubuntu, or they can operate as webservers (NGINX), or provide other functions like data structure servers or programming languages (Python, node, etc). Commond images include ubuntu, alpine, redis, nginx, centos, mongo.

Docker images are downloaded to the working directory. 

## Basic Docker Commands

docker run <IMAGE_NAME> - starts and runs a docker instance of the specified image

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
