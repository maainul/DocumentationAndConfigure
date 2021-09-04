1. What is docekr ?

BUILD, RUN, SHIP applications
	
Docekr is a platform/tools for building, running and shipping applications with a consistent manner.
That works development mechine and test and production mechine also. 
Docker enables you to separate your applications from your infrastructure so you can deliver software quickly. 

Reasons :

	1. One or more files missing
	
	2. Software version mismatch
	
	3. Different configurations
	
2. What is container?

An isolated environment for running an application.

Benefits :

	1. Allow multiple apps in isolation

	2. Are lightweight

	3. Use OS of the host
	
3. What is virtual machine?

An abstraction of a machine(Physical hardware)

Hypervisor is software to use to create or manage virtual machine.

Hypervisor:
	
	1. Vmware
	
	2. VirtualBox
	
	3. Hyper -V (only for windows)

By using hypervisor we can create multiple os

PROBLEMS:
	
	1. Each needs a full-blown os
	
	2. Slow to start
	
	3. Resource intensive
	
# Docker in Action

create directory and create file app.js

	mkdir smallapp

	cd smallapp

	touch app.js

```js
console.log("Hello Docker!");
```

## Dockerfile

```Dockerfile
# alpine = small version of linux to run node
FROM node:alpine  

# copy all files to the app directory ,if app directory is not avaiblabe then docker will create it
COPY . /app 

# assing all the acction will be perfomed in app directory
WORKDIR /app 

# general command
CMD node app.js

```

	docker build -t hello-docker .

	docker run hello-docker


## Linux Ubuntu

1. Pull images from hub

	docker run ubuntu

2. Start container intractive mode
	
		docekr run -it ubuntu

		root@2f759e6996e9:/#

		root ---> user

		2f759e6996e9 ---> container name

		/ --->  root directory

		# ---> root user

		$ ---> normal user

		echo hello

		whoami

		echo $0 ---> location of the shell program

		/bin/bash  ---> 

		bin --> folder/dirctory

		bin --> born in shell

		bash--> born again shell.. program
	
3. Install apt in linux container

		apt list

		apt update 

		apt install nano

		nano

		ctrl + x + n 

		apt remove nano

		ls

		ls -1

		ls-la

		cd ~

		pwd

4. Create directory and files In the linux.
	
		mkdir test

		mkdir -p a/b/c/d/ ---> create multiple folder


		mv test docker ---> rename   mv test(old folder name) docker(new folder name)

		touch hello.txt

		touch hello1.txt hello2.txt

		mv hello.txt hello-docker.txt ---> rename

		rm file*  ---> remove files name strarts with file....

		rm -r docker/ --> remove directory // r ----> recursive

		nano file1.txt (save files ctrl +x +Yes)

		cat file.txt  ---------> read data from the file.txt

		less 

		apt install less

		head -n 5 /etc/adduser.conf

		tail -n /etc/adduser.conf

5. Read and write files

		cat file1.txt > file2.txt  ---> read file1 and write data file2

		cat file1.txt file2.txt --> read multiple files

		cat file1.txt file2.txt > combined.txt ---> read two file and write into 1

		echo hello file1.txt

		ls -l /etc > files.txt

		cat files.txt

6. Search files and folders

		grep hello file1.txt  --> hello hello from file1.txt

		grep -i hello file1.txt --->case insencetive

		grep -i hello file*  ---> search in multiple files

		grep -i -r hello .

		grep -ir hello .

		find   ----> find directory and files

		ls -a ---> show hidden files

		find -type d

		find -type f

		find -type f -name "F*"

		find -type f -iname "f*" --> case sensetive

		find / -type -name "*.py"

		find / -type f -name "*.py" > python-files.txt

		cat python-files.txt
	
7. Multiple cmd
	
		mkdir test;cd test;echo done --> that will take to the test folder

		mkdir test && cd test && echo done ---> and operator --> if one cmd fails then other cmd won't be executed

		mkdir test || echo "Directory exits" --> and operator ---> create directory if not print message

		ls /bin | less

		ls /bin | head -n 5

		mkdir hello;\
		> cd hello;\
		> echo done

8. Env variables

9. Managing Process

		sleep 3 

		kill processid

		kill 38(processid)

10. Managing User

		useradd -m john

		cat /etc/passwd

		cat /etc/shadow

		usermod -s /bin/bash john

		docker exec -it -u john 2f78 

		add user

		groupadd developers

		cat /etc/group

		usermod -G developers john

		grep /etc/passwd

		groupadd artists

		cat /etc/passwrd | grep john

		grep john /etc/passwd

		groups john

		cat /etc/passwd

		usermod -G artists john
	
11. File Permissions:
	
		cd home

		echo echo hello > deploy.sh

		echo deploy.sh

		ls -l

		./delploy.sh

		chmod u+x deploy.sh 

		chmod o+x deploy.sh

		./deploy.sh

		chmod og+x+w-r *.sh
	
# Docker images

A image contains:

	1. A cut-down os
	
	2. Third-part libraries
	
	3. Application files
	
	4. Env variables
		
A container :

	1. Provides an isolated environment
	
	2. Can be stopped and restarted
	
	3. Is Just a process
	
## Simple react app

	sudo npm install -g create-react-app

	create-react-app react-app

	cd frontend

	yarn start


1. install node
2. npm install (install dependencies)
3. npm start

## Docekr files:
	contains instructions for building and image.
	FROM : Base image
	WORKDIR
	CORY
	ADD
	RUN
	ENV
	EXPOSE
	USER
	CMD
	ENTRYPOINT
	

```Dockerfile

FROM node:14.16.0-alpine3.13
```

	docker build -t react-app .

	docker image ls

	docker run -it react-app
	
	docker run -it react-app bash
	
	docker run -it react-app sh
	
	ls
	
	node --version
	

```Dockerfile

FROM node:14.16.0-alpine3.13
WORKDIR /app
COPY . . 
```	
	
create .dockerignore file in the cwd

node_modules

```Dockerfile

FROM node:14.16.0-alpine3.13
WORKDIR /app
COPY . . 
RUN npm install
```	

	docker build -t  react-app .
	
	docker run -it react-app sh
```
	
### Docker file with Expose
	
```Dockerfile

FROM node:14.16.0-alpine3.13
WORKDIR /app
COPY . . 
EXPOSE 3000

```

### Docker file with user

```Dockerfile

FROM node:14.16.0-alpine3.13
WORKDIR /app
COPY . . 
EXPOSE 3000
RUN npm install
RUN addgroup app && adduser -S -G app app
USER app

```
	docker run -it alpine

	useradd --> not present

	adduser --> present

	addgroup app

	adduser -S -G app app

	groups app

	addgroup mainul && adduser -S -G mainul mainul

	groups mainul

	
### Docker file with user

```Dockerfile

FROM node:14.16.0-alpine3.13
RUN addgroup app && adduser -S -G app app
USER app
WORKDIR /app
COPY . . 
RUN npm install
EXPOSE 3000
```

docker run react-app npm start

### Docker file with user

```Dockerfile
FROM node:14.16.0-alpine3.13
RUN addgroup app && adduser -S -G app app
USER app
WORKDIR /app
COPY . . 
RUN npm install
EXPOSE 3000
# Shell form
# CMD npm start
# Exec form
CMD ["npm", "start"] ----> we can override command
# ENTRYPOINT ["npm", "start"] ---> we can't give cmd outside
```
	docker run react-app

	docker history react-app



### Docker file with optimized build

```Dockerfile
FROM node:14.16.0-alpine3.13
RUN addgroup app && adduser -S -G app app
USER app
WORKDIR /app
COPY package*.json . 
COPY . .
RUN npm install
EXPOSE 3000
ENV API_URL = http://api.myapp.com/
CMD ["npm", "start"]
```

	docker build -t react-app .

## Removing images

	docker image prune

	docker container prune

	docker rmi imageId ---> remove image

## Tag

	docker build -t react-app:1 build .

	docker image remove react-app:1

	docker image tag react-app:latest react-app:1

	docker images

	docker build -t react-app:2 .

	docker image tag bo6 maainul/react-app:1 

	docker push maainul/react-app:1	
	
	
## Image Save and Load
	
	docker image save -o react-app.tar maainul/react-app:1
	
	docker image load -i react-app.tar
	
	docker images
	
## Docker Containers

	docker ps (process)
	
	docker run react-app
	
	docker run -d react-app (-d == run in the background)
	
	docker run -d --name blue-sky react-app
### Docker logs

	docker logs containerid
	
	docker logs --help
	
	docker logs -f containerid (-f saw realtime data)
	
	docker logs -n 5 containerid
	
	docker logs -n 5 -t containerid

### Docker port mapping

	docker run react-app
	
	docker run -d -p 3000:3000 --name c1 react-app (3000:3000)(hostPort:containerport)
	
	docker exec c1 ls (by exec we can run any cmd in a container)
	
	docker exec -it c1 sh

	pwd

	exit
	
### Stopping and starting Container

	docker stop c1
	
	docker ps
	
	docker start c1
	
	docker ps
	
What is the difference between start and run

By using docker run containerid ---> every time we create new container

By using docker start containerid ---> every time we are not create new container


	docker container rm
	
	docker rm c1
	
	docker stop containerid
	
	docker rm c1
	
	docker rm c1 -f
	
	docker ps -a | grep c1 (grab specific containers)
	
	docker container prune (all stoped container in one go)
	
### Container File System

	docker exec -it containerId sh
	
	ls | greap data
	
	
	
## Docker volumes
	
	 A volume is a storage outside of a container it can be directory in the host and cloud.
	 
	  docker volume 
	  	- create
	  	- inspect
	  	-ls
	  	-prune
	  	-rm
	  	
	docker volume ls
	
	docker volume inspect app-data(volumename)
	
### Starting a container and create a volume for parsesting data

	docker run -d -p 4000:3000 -v app-data:/app/data react-app
	
	docker exec -it 8d3edf sh
	
	docker build r-t ecact-app .
	
Volume is stored outside of the container

If we delete container this file still exists

	docker rm 007d -f
	
	docker exec -it ere09023 sh
	
	echo hello > log.txt
	
	exit

## Copy file from container to host.
	
	docker cp contaienrid:/app/log.txt .
	
## Copy host to container.
	
	echo hello > secret.txt
		
	
	docker cp secrect.txt ee2121:/app
	
## MAP project directory to a directory inside a container

map app-data volume to the /app/data directory inside a container

	docker run -d -p 5001:3000 -v $(pwd):/app -v react-app
	
	docker logs -f 696 


integration --> client ---> casa ---> (readAccountById...)

apppi/account/list/

core ---> (account)---> list--->listaccountbybranchid---> listaccountbranchid

api call ---> pass data



	
	
	
	
	
	
	
	
	


	
	
	
	
	
	
	
	
	






















