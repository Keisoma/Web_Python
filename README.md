# Web_Python

This project is a simple "Hello World" project used to illustrate a flask project, and using docker to containerize it?
## Steps to follow:

### Build the image
build the docker image with the following command:
`docker build -t test_web .`

This will create a docker image named test_web with the Dockerfile included with the project.

### Run a docker container
Instanciate the image in a docker container using:
`docker run -it -v $(pwd):/usr/src/app -p 5000:5000 --name web test_web`

It will run a docker container in interactive mode (input/output) with a mounted volume from the current folder $(pwd) to the file /usr/src/app in the docker container. We define the port 5000 for both the host machine and the docker container. The --name makes that the container's name isn't randommly generated and saves time not looking for the container id (docker ps). We instanciate the image we just created beforehand.

### Making sure the mount worked
#### Docker inspect
with `docker inspect web` we are going to make sure that the Mount worked. By scrolling up we would see a Mount section, in which we would see our mount, with the source and destination folder.

#### Docker exec
with `docker exec -it web sh` (sh since we are using an alpine image in the Dockerfile), we can enter the container. By entering the /usr/src/app/ folder, we can see the folder we mounted and if we change something in our source folder, it will also be changed in this folder inside the docker container.

