**Docker** allows you to install and run software irrespective of the installed dependencies and the operating system in use. This means your application can seamlessly run on any operating system without the headache of handling dependencies. No more trial and error, no more debugging — Docker simplifies the entire process.-</b>

Docker is a tool that enables you to install and run software effortlessly by abstracting away the complexities of dependencies and operating systems.-</b>


To run an application with Docker, you start by creating a **Docker file**. This file contains all the instructions necessary to install and run your application. It encapsulates the requirements, making the process reproducible and scalable.-</b>

**Building Docker Images**-</b>
Once the Docker file is ready, you build a Docker image. Think of the image as a compiled version of your application, complete with all the dependencies specified in the Docker file.-</b>

To execute your application with Docker, you use the simple **Docker run** command, specifying the image name and version tag. This results in the creation of a Docker container, a lightweight, isolated environment where your application runs seamlessly.-</b>




**NGINX** is open-source web server software. In this project I initialised nginx using docker. If you follow this tutorial make sure you have docker desktop on your local computer. I used visual studio code to run the commands.-</b>

Pull the offical image nginx from Docker Hub by running the following command:
**docker run -d nginx**

If you type: **docker images**, you should have the latest image downloaded.
To stop the container type: **docker stop "container id/name"**.
To remove the container: **docker rm "container id/name"**.


Port mapping is used to access the services running inside a Docker container. I opened a host port to give access to a corresponding open port inside the Docker container. Then all the requests that are made to the host port can be redirected into the Docker container

To publish a port for our container, I used the --publish flag ( -p for short) on the docker run command. The format of the --publish command is [host port]:[container port] . So, to expose port 80 inside the container to port 8080 outside the container, I passed 8080:80 to the --publish flag

Create containers based on nginx image with ports mapping, do the following: **docker run -d -p 8080:80 nginx** (use any available host port:container ports, in my case I used the one as mentioned)

To make connection to the nginx container do the following: go to web browser, type localhost:8080, and you should see a welcome to nginx web page. Now you are able to connect to the application inside the container using the external port of your computer(i.e the host). The nginx html web page is located inside the container

Stop the container type: **docker stop "container id/name**.
Remove the container: **docker rm "container id/name"**.


**Enabling Volumes mapping for nginx container**
Using visual studio code, cd into 1.nginx folder, then run the following command:

**docker run -dit -p 8888:80 -v ${PWD}/html:/usr/share/nginx/html nginx**.

This command runs in detached mode and interactive terminal (-d, -i, -t flags used), with host port 8888 and conatiner port 80 which is open by default from nginx, mapping -v (volume) to the directory pathway (i.e specify the folder within the container), using the nginx image.

Type **docker inspect "image ID"**, which will give info about volume mapping. This shows any folder which is on local computer can be read/write by the container. So any processes which takes place within the container in terms of write, will also write to the local folder on the computer.

If you go to web browser, type **localhost:8888**, you should see a Welcome to custom NGINX web page as written in the index.html file. If you modify the index.html file to "update custom NGINX web page", the change is immediate, refresh web page and see change.

If you want to run another container, then run the same command as previous, but this time change local host port to say 8889 and everything else the same. Now you will have two containers running and mapped to the same volume. 
If you run a container with a database and insert some records in it then it is stored in the container. If the container is stoped then all data is lost. So if you create another container with the same image, database, you will not have any data from the previous container, it will be empty.

Anotherway to map volume to the application (nginx) is to have both vol and app inside the container, and the volume on the local host is mounted on the conatainer which will store the data. This allows the data within the volume to persist

Make sure to stop and delete all containers and image

**docker ps -a -q** - gives you lists of all container ID

**docker stop $(docker ps -a -q)** - stops all containers

**docker rm $(docker ps -a -q)** - deletes all containers
