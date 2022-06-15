# Docker Notes

Overview of an OS

software(s) / Process(es) => System Call => Kernal => [ CPU | Memory | Hard Disk ]

Name spacing: isolating resources per process 
Control groups: limit amount of resources used per process
(specific to linux os)

example:
install redis `docker run -it redis`
Docker cli reaches out to docker hub, to download a single file called *image* which contains all the dependencies and configurations required to run a very specific program, e.g redis.
We can use an image to create a *container* which is an instance of an image, we can think of it as a running program.

image: file system snapshop + startup command

Basic Command:
`docker run hello-world`
Docker Client -> Docker Server <-> Docker Hub
Docker Server -> Creates a container and runs the hello-world program

`docker version` - docker version
`docker run <image name> <command>` - override
example: `docker run busybox echo hi there`
         `docker run busybox ls`
`ls` spits out folder solely for the container.
`docker ps` - list all the running containers
`docker ps --all` - list all the containers ever created
`docker run` = `docker create` + `docker start` - create a container + start a container
`docker create <image>` - returns an id
`docker start <id> -a` - `-a` watch for output and print it out on terminal
`docker system prune` - delete stopped containers and build cache
`docker logs <container id>` - get logs from a container
`docker stop <container id>` - SIGTERM for clean up etc. 
`docker kill <container id>` - SIGKILL for immediately shutdown.
`docker exec -it <container id> <command>` - to execute a docker container (running).
example: `docker exec -it 4617a4e81d42 redis-cli`
`-it` - -i & -t, -i attach terminal, -t show text in a formatted
`docker exec -it <container id> sh` - open terminal
`docker run -it <image name> sh`

Create an image
Dockerfile -> Docker Client -> Docker Server -> Usable Image

Dockerfile(flow):
1. Specify a base image
2. Run some commands to install additional programs
3. Specify a command to run on container startup

Creating a dockerfile:
```
FROM alpine # image as a base
RUN apk add --update redis # download redis
CMD ["redis-server"]
```
for nodejs:
```
FROM node:alpine
WORKDIR  /usr/app
COPY ./package.json ./ # from local to container (speeds up build process)
RUN npm install
COPY ./ ./
CMD ["npm", "start"]
```

Build the dockerfile:
```
docker build .
```
or
```
docker build -t docker_id/project_name:latest .
```
? optional for container already running.
```
docker commit -c 'CMD ["redis-server"]' <container id>
```

Run the container
```
docker run <docker id>
```
```
docker run  docker_id/project_name
```

Port Forwarding
```
docker run -p 8080:8080 <image id>
```
(outside:inside)
