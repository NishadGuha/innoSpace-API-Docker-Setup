# innoSpace-API-Docker-Setup
This repository contains the setup files for the locally hosted docker environment which runs the API that was built for the project. The technology stack used is nginx-php7.4-mysql8-node-docker.

## Setup
Please make sure you have setup docker on your local machine. Check: [Get Docker](https://docs.docker.com/get-docker/)\
\
In case you are running a windows system, please make sure to have virtualization enabled in your BIOS and have [WSL-2](https://docs.microsoft.com/en-us/windows/wsl/install) installed since docker runs on the linux subsystem only. In case you are running a linux or macOS machine, then you don't need to worry about setting this up.\
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
In order to install all PHP dependencies, run the command:
```
docker-compose exec php74-service composer install
```
### Database
In order to run database migrations, run the command:
```
docker-compose run --rm php74-service php bin/console doctrine:migrations:migrate
```
In case you ran into issues executing the migrations, you might need to create a database by using the command
```
docker-compose run --rm php74-service php bin/console doctrine:database:create
```
Then run the migrations again.
### Testing
In order to run all the unit tests, run the command:
```
docker-compose exec php74-service php ./vendor/bin/phpunit
```
Once you are done using the API, you can stop the docker containers using the command:
```
docker-compose stop
```
## Additional Commands
Once you are running the containers already, in order to restart the containers, you can run the command:
```
docker-compose restart
```
If you want to stop the containers and CLEAR THE DATABASE, you can run the command:
```
docker-compose down
```
In order to access the PHP bash through the docker container, run the command: (exit using control + D)
```
docker exec -it php74-container bash
```
In order to query the database, run the command:
```
docker-compose run --rm php74-service php bin/console doctrine-query-sql
```
## Accessing the API
It is highly recommended to use an API client such as [Postman](https://www.postman.com/downloads/) or [Insomnia](https://insomnia.rest/download) in order to access and use the different routes and functionalities of the API.\
\
The API will be hosted by default on you local machine, on port 8080. Hence, the default url to access the API is: http://localhost:8080/api
\
Please ask the author for further documentation regarding accessing the different routes of the API.
