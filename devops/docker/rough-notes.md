# DOCKER

## TOPICS

Images
Container
Volume mount
Bind Mount

## Installation

go to link https://www.docker.com/ and click download for desktop based on which os your using also (check device specification)

### Docker hub

docker hub is the place docker container is publsihed

### Checking

```bash

docker
docker run docker/whalesay  cowsay "Hi team i am checking"


## if wsl is old

wsl --update
wsl --shutdown
wsl --version



```

connecting to postgress

```bash

docker run --env POSTGRES_PASSWORD=foobarz --publish 5122:5122 postgress@latest
x
docker run --name my-postgres   --env POSTGRES_PASSWORD=foobarz   --publish 5122:5432   --rm -d postgres:latest
```

## Commands

```bash


docker pull
docker images
docker run
docker ps
docker ps -a
docker stop
docker rm
docker rmi
docker exec
docker logs


docker stop 12312


## remove all container
docker rm $(docker ps -aq)

## remove all images


docker rmi $(docker images -q)


## disk usage
docker system df



```
