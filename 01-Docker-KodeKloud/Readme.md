Source: KodeKloud
Course Link: https://learn.kodekloud.com/courses/crash-course-docker-for-absolute-beginner

1. Docker originally utilized Linux Containers (LXC) as its container execution driver in its early versions. 
However, Docker later developed and migrated to its own container runtime environment, libcontainer, which now powers Docker containers by default.

2. To get the info on Docker CLI, run the command docker --help. Observe the options listed.

3. Spin up a Docker container using the Ubuntu image.\
Note: Use the docker run command for this task.
```
docker run ubuntu
		OR
docker run -it ubuntu bash 
```

4. The container that was started in the previous task is currently in an exited state. This occurs because a process needs to be run within the container to keep it alive.\
You can verify the status of the container using the following command:
```
docker ps -a     
```

5. Delete all containers from the Docker Host, both Running and Not Running ones.\
Note: Remember you may have to stop containers before deleting them.
Note: Be careful while running this commands
```
docker stop $(docker ps -aq)
docker rm $(docker ps -aq)
```

6. Cleanup: Delete all images on the host. Remove containers as necessary.
This command stops and removes all currently running containers.
```
docker stop $(docker ps -aq)
docker rm $(docker ps -aq)
```
Remove all images
```
docker rmi $(docker images -aq)
```

7. Run a container in detached mode with the nginx:1.14-alpine image and name it webapp. \
Note: Use --name flag to name the container.
```
docker run -d --name webapp nginx:1.14-alpine
```

8. An Ubuntu-based container running on the terminal. Create a file learning.txt under the root folder with the text This is the file.
```
# Check running containers
docker ps

# Enter the Ubuntu container
docker exec -it <container_name> bash

# check pwd, and move to root folder if necessary using cd command.
# Create the file in root folder
echo "This is the file." > ./learning.txt

# Verify
cat /learning.txt
```


Some commands:\
ps - list containers
```
docker ps
```
ps -a => to see all containers
```
docker ps -a
```
STOP - stop a container
```
docker stop <container_name>
```

rm - Remove a container

```
docker rm <container_name>
```

images - list images
```
docker images
```

remove the image
```
docker rmi <image_name>
```

docker pull => Downloads an image from Docker Hub to your computer.
Think: “Just download the file.”
Ex:
```
docker pull python:3.10
```

docker run => Runs a container from an image. If the image is not downloaded, Docker automatically pulls it first.\
Think: “Download (if needed) + start the app.”\
Ex:
```
docker run python:3.10
```
Exec => Execute a command
Ex:
```
docker exec -it mycontainer bash
```
This opens a shell inside the running container.\
exec = execute something inside a running container\
run = start a new container
