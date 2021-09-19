<div align="center">
  <h1> How to create own Docker Image using Commit command </h1>
</div>

### Step 1. Launch a container 
```
docker run -i -t  --name <Container_name>  <Image_name>:<versions>
```

### Step 2. Inside that Container install the softwares or create your own program according to your requirement.

### Step 3. Create a Docker image using commit command
```
docker commit <Container_name_that_launched_above> <your_image_name>:<version>
```

### Step 4. Now launch a container using above created Image
```
docker run -i -t  --name <Container_name>  <your_image_name>:<versions>
```

**Note**: you can launch any number of container using above created Image and that container have all the program that are inside our older container.
