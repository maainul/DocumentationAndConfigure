# Docker

## 1. Continers

1.  Run a container

        docker run hello_world : it will download a container and run if locally is not available

2.  Show the status of docker

        systemctl status docker

        systemctl start docker

3.  How to create a simple container from CMD:

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

# Docker

## 1. Continers

1.  Run a container

        docker run hello_world : it will download a container and run if locally is not available

2.  Show the status of docker

        systemctl status docker

        systemctl start docker

3.  How to create a simple container from CMD:

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

![5 docker-system](https://user-images.githubusercontent.com/85335954/129874163-39b7d83c-c281-4e2a-8c17-d3b9f9e4a501.png)

## Docker Ecosystem

![1 docker-ecosystem](https://user-images.githubusercontent.com/85335954/129873377-9a8e6448-a72d-491b-ae70-bf3be8d28be6.png)

## Docker Cli and Daemon intraction

![2 Dockerclianddockerdaemon](https://user-images.githubusercontent.com/85335954/129873530-7380bfab-c1b8-4d77-8e7a-4c4947bb2599.png)

1. Create and Run a container

![3 dokcer-run-with-dockerhub](https://user-images.githubusercontent.com/85335954/129873683-8ab8d95f-a7a5-40de-b2a7-564580432e90.png)

    docker run busybox echo Hi there

## Image and Container

![4 docker-image and container](https://user-images.githubusercontent.com/85335954/129874030-909a2104-6612-4271-9971-133199f59c39.png)

2.Run a container

![6 docker-run](https://user-images.githubusercontent.com/85335954/129874227-b2c5739f-5c38-4b07-bb36-a66f64090572.png)

    docker run busybox ls

3.List of all container

    docker ps

4.Run a container with google ping

    docker run busybox ping google.com

5.List of all container

    docker ps -a

## Create and Run

![7 create-run](https://user-images.githubusercontent.com/85335954/129874270-1e661931-b172-4c54-9fa0-7790178eeee5.png)

6.Just create a project

    docker create hello-world

7.Start and execute project

    docker start -a 987aeb324b54i0

8.It will only start a project not execute

    docker start 987aeb324b54i0

9.Remove all container(Caution)

    docker system prune

10. Logs of docker container

![8 logs](https://user-images.githubusercontent.com/85335954/129874358-d3501d46-af5e-46f1-9740-e3592dc712b2.png)

    docker logs 98pef4g464 (containerId)

11. Stopping a Continer

![10 stop-and-kill](https://user-images.githubusercontent.com/85335954/129874437-1524350e-cab1-47b8-8b66-e29903681588.png)

Little bit time to stop.10 sec need to stop a container

    docker stop 98pef4g464

You have to shutdown now.No time needed

    docker kill 98pef4g464

## Install Redis image

12.Create and run redis db

    docker run redis

It will show an error.Because our redis-cli is not in the docker container.So we have to integrate this with docker container

    redis-cli

13. Execute commands in Running containers.

![additionalcommand](https://user-images.githubusercontent.com/85335954/129874509-b0ed44ef-febd-46a4-b8ac-b8ffffc20dce.png)

By Using the exec cmd we can run a second running program inside out container.
docker exec -it 98pef4g464 redis-cli

interactive with terminal

    docker exec -t 98pef4g464 sh

14.starting with a shell

    docker run -it busybox sh

## DOCKER FILE

15. create docker filet to install redis-server

![file-1](https://user-images.githubusercontent.com/85335954/129885460-edb1ea25-5ef8-446a-8798-a9f9821d8917.png)

    docker build .

![file2](https://user-images.githubusercontent.com/85335954/129890758-41626c21-c740-4844-8a8e-6c700a0a4dd6.png)
![file-3](https://user-images.githubusercontent.com/85335954/129890762-c468defe-6cd5-4b62-ac73-ec288f4d0171.png)

16.

## Install Docker Container From Dockerfile Node

17. Project Flow
    ![steps](https://user-images.githubusercontent.com/85335954/130178039-578378cf-c5f6-48e0-b569-123af38cbdb9.png)

18. Project Structure
    ![nodef1](https://user-images.githubusercontent.com/85335954/130178100-52add70e-3ce2-414b-ad3a-caf520aac458.png)

19. Index.js
    ![node-2](https://user-images.githubusercontent.com/85335954/130178197-98ea4b74-bdf6-4a95-93a4-b6de0aff2bad.png)

20. Dockerfile
    ![node-dockerfile](https://user-images.githubusercontent.com/85335954/130178156-332574ae-0985-4e7c-a264-5dc2daaf6241.png)

#### Run CMD :

    docker build .

Error will happend

### LET'S Fix the issue

Update Dockerfile

![nextnode](https://user-images.githubusercontent.com/85335954/130180642-c2513e0b-fef4-45a2-851d-b452fbe07a94.png)

    docker build .

Now it is fixed.

## COPY file to the container

    COPY ./ ./

```
    # Specify a base image
    FROM node:alpine

    COPY ./ ./
    # Install some dependencies
    RUN npm install

    # Default command
    CMD ["npm","start"]
```

## Run cmd with tag

    docker build -t maainul/simpleweb

    docker run maainul/simpleweb

    docker run -p 8080:8080 maainul/simpleweb

### Let's test in the web browser

    localhost:8080

Not working .... PORT MAPPING

## Port Mapping

![portmapping](https://user-images.githubusercontent.com/85335954/130363208-c887de9d-22bc-467e-89f4-d48284a6fd8a.png)

![portmapping-2](https://user-images.githubusercontent.com/85335954/130363238-79395163-0f90-4e7c-9345-4577bca45838.png)

![portmapping-3](https://user-images.githubusercontent.com/85335954/130363244-bff85d06-989c-4e17-928d-100c07e2c9ca.png)

Host port and docker container port can be different

    Let's try

    docker run -p 5000:8080 maainul/simpleweb

    localhost:5000

## Question : Can I change the port of container ?

Yes.

    docker run -p 5000:6000 maainul/simpleweb

But wait a minute change port number from the project

Before :

```node
app.listen(8080, () => {
  console.log("Listen on port 8080");
});
```

After :

```node
app.listen(6000, () => {
  console.log("Listen on port 8080");
});
```

## Update the dockrfile

Update the dockerfile because all file is in the root directory of container

![-itflag](https://user-images.githubusercontent.com/85335954/130363414-c8c11d27-a4bf-467e-9d2a-4c24fbcbaef6.png)

It can be conflict so let's update docker file...

# Where project will be saved

WORKDIR /usr/app

## Full Dockerfile

```
# Specify a base image
FROM node:alpine

# Where project will be saved
WORKDIR /usr/app

COPY ./ ./
# Install some dependencies
RUN npm install

# Default command
CMD ["npm","start"]
```

    docker build -t maainul/simpleweb .

    docker run -p 8080:8080 maainul/simpleweb

    docker ps

    docker exec -it idofcaontainer sh

    ls
    cd /
