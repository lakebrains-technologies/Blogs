
<img src="https://github.com/lakebrains-technologies/Blogs/blob/master/Docker_Cheatsheet/images/Docker.png?raw=true">

# Docker
- Container type used here is LxC
- Consists of isolated containers that share the underlying kernel.
- These are faster as compared to Virtual Machines and take less space as they dont have complete another os installed. 


## Getting Started with Docker:
#### Official website for installation and other references : [Docker official Website]("docs.docker.com")

### Basic Commands:
 ```docker run <image name>``` : runs the image and mounts it as a container. If the image is not present locally it reaches out to dockerhub and downloads the image.

```docker run <name> sleep <time(s)> ``` : puts the container on sleep for t seconds

 ```docker ps``` : lists all running containers with some basic details.

 ```docker ps -a ``` : lists all the running and not running containers.

 ```docker stop <name>``` : stops the docker with that name. If name is not known run the docker ps command to see the names.

 ```docker rm <name>``` : deletes the docker container permanently. 

 ```docker images``` : list of all the available images on the system.

 ```docker rmi <name>``` : to remove the docker image. NO CONTAINERS SHOULD BE RUNNING FROM THAT IMAGE. 

```docker pull <name>``` : just pulls the image and not run the container.

```docker exec <name> <command>``` : runs the command in that container.

```docker run <application>``` : runs the application in the docker and shows the outputs in the terminal.(attaches the app to the terminal.)

```docker run -d <application>``` : runs the application in the docker and doesnt show the output anywhere. (App runs in the background i.e. detached from the terminal.)

```docker attach <name>``` : to attach the application later.




#### Docker Run Commands: 
```docker run redis``` : this will run latest version of redis.

```docker run redis:3.5``` : this will run the given version.

**NOTE** : Docker container doesnt listen to the Standard Input. To give the application inputs, you should use the flag -i
 
```docker run -i <application>``` : takes the required inputs for the application to run. But it still doesnt give the prompts.

```docker run -it <application``` : attaches the application to the terminal and runs normally.

##### Run - Port Mapping :
Every docker container gets an ip assigned. But that is a local IP & can be accessed only within the docker host. For users outside docker container, we can use IP of the docker host to a free port on the docker host.
This is k/a port mapping.
```
Docker host -----------------> free port 1
    |------------------------> free port 2
    |------------------------> free port 3 -----> mapped to port inside docker container.



For Example: 

The *local IP* given to the application is 0.0.0.0:5000 where 5000 is local port inside the docker container. 
*Docker Host* is 192.168.1.5
*Free Port* used on the *Docker Host* 80
80 must be mapped to 5000 known as **Port Mapping**

```

```docker run -p 80:5000 <application>``` : Port mapping

User can use the url http://192.1681.5:80 and it will be then routed to port 5000 in the docker container.
Thus you can run many application this way.


##### Run - Volume Mapping : 
When you run an image within a container, all the files you change and create will be done in the container. And when you delete the container all the data goes away. 
To deal with this volume mapping is done. If you would like to persist data, you should map a directory outside of docker container to a directory inside the docker container
```docker run -v <dir_outside_container>:<dir_inside_container> <image name>``` : volume mapping syntax

Example:
```docker run -v ~/my-recognition-python:/my-recognition/python mysql```


##### Docker Inspect :
```docker inspect <name>``` : gives detailed information about the container.

##### Docker Container Logs: 
```docker logs <name>``` : docker logs that are given in the standard output.


#### Environment Variables
Some variables have to be set in code internally and to change any minute functionality you have to change the code. This problem can be solved by setting environment variables.

inside the code use ```color = os.environ.get("<variable_name>")```
to set this run this ```export <variable_name>=blue``` -> and then run the application

```docker run -e <variable_name>=blue <application>``` : this will export the variable with given value and then run the application inside the docker container.

### Docker Images :
Here, we'll learn how to create docker images.
If we were to setup things mannually without a docker, we would have done these things:
1. OS - UBUNTU
2. Update apt repo
3. Install dependencies using apt
4. Install dependencies using PIP
5. Copy source code to /opt/ folder
6. Then run the application.

We have to do all those things while creating the images:
EXAMPLE:
##### Dockerfile
```
FROM Ubuntu

RUN apt-get update
RUN apt-get install python

RUN pip install flask
RUN pip install flask-mysql

COPY . /opt/source-code

ENTRYPOINT FLASK_APP=/opt/source-code/app.py flask run
```
```docker build Dockerfile -t siddharth/my-custom-app``` : build a dockerfile and create an image locally on the system

```docker push <image_name>``` : to make this image available on the dockerHUB

**NOTE** : First line states the OS to use, and hence it is very important. Every dockerfile starts with *FROM*.

```docker history <image Name>``` : gives details like created date, created by, and size etc.

**NOTE** -  If particular command fails, the cache memory is used to continue rebuilding image. Hence it continues from where it is left off.

```docker run <image_name> cat /etc/*release*``` : to check basic details like underlying OS used etc.

### Conclusion 
We studied the basic docker commands, that might come handy when we use it. This article will soon be updated with more commands and there detailed explaination.


#### Reference link: 
- [Youtube - Docker Tutorial](https://www.youtube.com/watch?v=fqMOX6JJhGo) by freeCodeCamp




