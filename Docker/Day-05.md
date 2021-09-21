<div align="center">
  <h1> Docker Compose  </h1>
</div>


## What is Docker Compose
Docker Compose is a Docker tool used to define and run multi-container applications. With Compose, you use a YAML file to configure your application’s services and create all the app’s services from that configuration.

### Features of Docker Compose 

👉 Multiple isolated environments on a single host <br>
👉 Preserve volume data when containers are created <br>
👉 Only recreate containers that have changed <br>
👉 Orchestrate multiple containers that work together <br>


### **Docker compose installation Link :** https://docs.docker.com/compose/install


### To check the Version of Docker compose
```
docker-compose version
``` 

### To Start the Docker Compose
```
docker-compose start
```

### To stop Docker compose
```
docker-compose stop
``` 

### To see additional information about arguments and implementation details
``` 
docker-compose <command> --help
``` 

### To build images in the docker-compose.yml file.
```
docker-compose build
``` 

### List all images
```
docker-compose images
``` 

### This command create containers from images built for the services mentioned in the compose file
```
docker-compose run
``` 

### This command does the work of the docker-compose build and docker-compose run commands.
```
docker-compose up
``` 

### List all the containers
```
docker-compose ps
```

### To delete all the containers, networks, and images.
```
docker-compose down
```
