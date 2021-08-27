## Docker For Netbank

	docker-compose up --build -d

	docker logs -f netbank_cms

	docker-compose build netbank-cms

	docker restart netbank_cms

	docker-compose up -d


## Clone a project
	
	git clone 

	git remote add upsteam git@git.brankas.dev:netbank/netbank.git

## How to stop postgres

	sudo service postgresql status

	sudo service postgresql stop

	sudo service postgresql status

  

11. If any Changes happend then run these cmd for docker

	sudo docker restart netbank_cms

	sudo docker-compose up -d
	
	
git pull upstream master

git checkout -b NV-123-Test

# Push

	git status
	
	git add .
	
	git commit 
	
	git checkout origin master --->( go to the master branch and pull)
	
	git pull upstream master
	
	git checkout branch_name
	
	git rebase master
	
	git push branch-name -f

## Update Commit message


	git add .
	
	git commit --amend
	
	git push origin NV-165-create-hubspot-on-profile --force


	DATABASE_CONNECTION="user=postgres password=secret host=localhost port=5435 dbname=test sslmode=disable" go test

	DATABASE_CONNECTION="user=postgres password=secret host=localhost port=5435 dbname=test sslmode=disable" go test -c
	

## Merge Conflict
	
	git checkout master
	
	git pull upstream master
	
	git checkout NV-360-somenthig-branch-name
	
	git rebase master
	
	git add .
	
	git rebase --continue
	
	git commit 
	
	git push origin NV-something-name -f
	

## Netbank Work Flow

	GUNK-----> gunk/Profile ---->Gunk Service 

	This Service is implemented in Profile/services/profile/ folder

	This Service database Related stuff in profile/core/profile/company.profile

	This method will call profile/storage/postgres/companyprofile.go

	(Interface)-------> (service)---------------------> (Repository)--------------> (database)
	
	gunk/profile ---- > profile/services/profile -----> profile/core/profile -----> storage/postgres



handler --> (assign path) (and method name)

add file to the handler folder



Business logic -----------------> in the core folder

# How to push Data

	git status
	
	git commit 
	
	git log
	
	git checkout master
	
	git pull upstream master
	
	git checkout NV-39-signup
	
	git rebase master
	
	git status

	git push origin NV-39-signup


# Push Second time

	git status
	
	git add .
	
	git commit --amend 

	ctrl + O + Enter + ctrl + x

	git push origin NV-ticket name --force


# Staging push

	git push upstream your-branch:staging-test -f



## grpc add


	go get -u google.golang.org/grpc

## Add protoc

	go get -u github.com/golang/progobuf/protoc-gen-go



## Docker install and run postgres:12-alpine

	docekr pull postgres:12-alpine

	docker images

	docker image ps

	docker run --name postgres_for_book -p 5430:5430 -e POSTGRES_USER=root -e POSTGRES_PASSWORD=secret -d postgres:12-alpine

	docker container ps -a

	docker exec -it postgres_for_book psql -U root
