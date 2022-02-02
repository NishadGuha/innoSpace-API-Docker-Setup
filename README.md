# innoSpace-API-Docker-Setup
nginx-php7.4-mysql8-node-docker-network

## Setup
This repository contains the setup files for the locally hosted docker environment which runs the API that was built for the project. Please make sure you have setup docker on your local machine. Check: [Get Docker](https://docs.docker.com/get-docker/)\
\
In case you are running a windows system, please make sure to have virtualization enabled in your BIOS and have WSL-2 installed since docker runs on the linux subsystem only. In case you are running a linux or macOS machine, then you don't need to worry about setting this up.\
\
After you make sure that docker is running on your system, ``cd`` into this repository on your local machine and execute the following commands:
```
docker-compose up -d --build
```
This command will build all the images and containers and set it up on your machine. It might take a while to execute this command as the docker cli will download and pull all the images that are necessary to build the containers.
In the future, you can remove the ``--build`` flag and only execute the command:
```
docker-compose up -d
```
Once you are done using the API, you can stop the docker containers using the command:
```
docker-compose stop
```
## Additional Commands
Once you are running the containers already, in order to restart the containers, you can execute the command:
```
docker-compose restart
```
If you want to stop the containers and CLEAR THE DATABASE, you can run the command:
```
docker-compose down
```
## Accessing the API
It is highly recommended to use an API client such as [Postman](https://www.postman.com/downloads/) or [Insomnia](https://insomnia.rest/download) in order to access and use the different routes and functionalities of the API.\
\
The API will be hosted by default on you local machine, on port 8080. Hence, the default url to access the API is: http://localhost:8080/api
\
Please ask the author for further documentation regarding accessing the different routes of the API.
