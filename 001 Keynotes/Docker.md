#coding 
Docker is a container tool which helps solve the problem of "It works on my system". It help clone projects from one system of any OS to another completely different system with the same dependencies and same versions, even mimicking the OS.
- It has 2 types `docker-container` and `docker-image`, the container is a collection of the project and its dependencies where as and image is a snapshot that helps docker load in these containers
### Flags
- `-it` the interactive mode allows the user to access containers terminal.
- `<image-name>:<tag>` will pull that taged image from the website.
- `-d` runs the container in the background.
- `-e` is used to declare environment variables.
- `--name`: to name a container
### Commands:
- `docker run -it <image-name>` : creates and runs a OS in interactive mode (like being able to use terminal)
- `docker pull <image-name>`: Pulls the image from docker website.
- `docker images`: List all available images.
- `docker run --name <container-name> <image-name>`: Create a new container with the given name and run it 
- `docker ps -a`: Lists all containers available.
- `docker ps`: Lists all running containers.
- `docker start <CONTAINER-ID>`: Starts the container with the proper ID.
- `docker stop <CONTAINER-ID>`: Stops the container with the proper ID.
- `docker rmi <image-name>`: Removes/ Destroys the given docker image.
- `docker rm <container-name>`: Removes/ Destroys the given docker container.

#### Lazy Docker