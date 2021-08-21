# Docker 

## 1. Continers

1. Run a container
	
		docker run hello_world : it will download a container and run if locally is not available

2. Show the status of docker 
	
		systemctl status docker
	
		systemctl start docker

3. How to create a simple container from CMD:
	
		docker run -t -t --name "MY First Container" centos:latest /bin/bash


	- i = iteractive mode
	- t = terminal

	bin/bash = cmd or server to run in the container to use

	show the host file : hostname -f, top

(Now we are inside the container terminal)

	
	docker container ls : list of all containers
	
	docker container ls -a : list of all running container

## 2. Images

	docker image list

	docker pull ubuntu (hun.docker.com)

## 3. Docker file

Docker file is a simple text file contain list of instructions or steps to build new docker images.


Create a folder inside directory
	
	mkdir dockerbuild
	
	cd dockerbuild
	
	vim Dockerbuild

```bash
FROM ubuntu:latest
MAINTAINER "Mainul Hasan"

RUN apt-get update
RUN apt-get install -y openssh-server

CMD["echo","Hello World........."]
```



type : esc + wq !

From this docker file we can build container

	docker build -t myubuntu:1.0


Run Docker :
	
	docker run myubuntu:1.0

See running containers : 
	
	docker continer ls

See all containers :
	
	docker container ls -a

## Remove Containers 

	docker container rm containerID

## Create apache2 images and container
	
	mkdir apachedockerfolder

	cd apachedockerfolder
	
	vim Dockerfile

## Dockerfile.yaml
```
# This is test file for dockerfile for apache2 container and images

FROM ubuntu:latest
ARG DEBIAN_FRONTEND=noninteractive
MAINTAINER "mainul hasan"

RUN apt-get update
RUN apt-get install -y apache2

RUN mkdir -p /var/lock/apache2
RUN mkdir -p /var/run/apache2

ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_PID_FILE /var/run/apache2.pid
ENV APACHE_RUN_DIR /var/run/apache2
ENV APACHE_LOCK_DIR /var/lock/apache2
ENV APACHE_LOG_DIR /var/log/apache2
ENV LANG C

CMD ["/usr/sbin/apache2","-D","FOREGROUND"]

EXPOSE 80


```
	docker run -t -d -P --name apache2Container apache2ubuntu

	-d = detachablemode
	
	-P = portmapping

## Docker Compose

We may have multiple continers we have to manage multiple containers.

Docker compose is a tools for defining and running multi-continer 
docker application.

Use yaml file to configure applications

With single command we should be able to build and start containers

Terminationg containers also easy by executing single containers

	
	docker compose

	docker-compose up -d

	docker-compose down

## Create mysql and nginx

	mkdir docker-compose

	cd docker-compose

	vim docker-compose.yaml

```
version: '3'
services:
        mysql_database:
                image: "mysql:latest"
                environment: 
                        - MYSQL_ROOT_PASSWORD="password"
        
        web_test :
                image : "nginx:latest"



```
### Create a container from compose

	docker-compose up

### for stop a container go to the docker compose directory and apply cmd

	docker-compose down




# -------------------------DOCKER--------------------------------------------- 

1.Create and Run a container

	docker run busybox echo Hi there

2.Run a container

	docker run busybox ls

3.List of all container

	docker ps

4.Run a container with google ping

	docker run busybox ping google.com

5.List of all container
	docker ps -a

6.Just create a project

	docker create hello-world

7.Start and execute project

	docker start -a 987aeb324b54i0  

8.It will only start a project not execute

	docker start 987aeb324b54i0

9.Remove all container(Caution)

	docker system prune

10.Logs of docker container

	docker logs 98pef4g464 (containerId)

11.Stopping a Continer
	
	docker stop 98pef4g464 ---> little bit time to stop.10 sec need to stop a container

	docker kill 98pef4g464 ---> You have to shutdown now.

12.
