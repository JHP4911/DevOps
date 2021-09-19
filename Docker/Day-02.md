<div align="center">
  <h1> Some Useful Docker Commands </h1>
</div>


### To check the Version of Docker
```
docker version
``` 

### To check whether docker is running on your system or not(For linux users)
```
systemctl status docker
```

### To Start the Docker Service
```
systemctl start docker
```
**NOTE:** The above command start the docker service at **Runtime**. Means, if the system reboot , the service again stop and we have to again start the service. 

### To permanently enable the docker service
```
systemctl enable docker
```

### Shows detail information about docker
```
docker info
``` 

**NOTE:** If we want to launch Operating System(OS) , we need **OS Image**. Similarly, in **Docker world**, if we want to launch any OS in docker , we need **Docker Image**.
**In Docker World, OS is known as Container**.


### Download an Image
```
docker pull <Image_name>:<versions>
```

**NOTE:** Docker Community have their own internet location or url. They put all the main OS images like RedHat, centos, ubantu, etc at one website known as Repository/Registry or Docker Public Registry. That location name is **hub.docker.com**  

### List All Docker Images
```
docker images
``` 

### To launch a docker container 
```
docker run -i -t  --name <your_Container_name>  <Image_name>:<versions>
```

### Shows Running containers
```
docker ps
``` 

### Start a docker container
```
docker start <Container_name>/<container_ID>
``` 

### Login to a docker container
```
docker attach <Container_name>/<container_ID>
``` 
**NOTE:** There are two ways to stop the container. 
1. If we are inside the container --> use **exit** command
2. If we are outside the container, means if we are in base OS --> use **stop** command

### Stop a docker container
```
docker stop <Container_name>/<container_ID>
``` 

### Shows All the Containers - Running and Stopped
```
docker ps -a
``` 

### Delete a Container
```
docker rm -f <Container_name>
``` 

### Delete All the Containers - Running and Stopped
```
docker rm -f $(docker ps -a -q)
``` 

### Delete a docker Image
```
docker rmi <image_name>
``` 

### Delete All the Images
```
docker rmi $(docker images -q) 
``` 




