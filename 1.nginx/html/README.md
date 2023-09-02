NGINX is open-source web server software. In this project I initialised nginx using docker. If you follow this tutorial make sure you have docker desktop on your local computer. I used visual studio code to run the commands.

Pull the offical image nginx from Docker Hub by running the following command:
docker run -d nginx

If you type: docker images, you should have the latest image downloaded
To stop the container type: docker stop "container id/name"
To remove the container: docker rm "container id/name"


Port mapping is used to access the services running inside a Docker container. I opened a host port to give access to a corresponding open port inside the Docker container. Then all the requests that are made to the host port can be redirected into the Docker container

To publish a port for our container, I used the --publish flag ( -p for short) on the docker run command. The format of the --publish command is [host port]:[container port] . So, to expose port 80 inside the container to port 8080 outside the container, I passed 8080:80 to the --publish flag

Create containers based on nginx image with ports mapping, do the following: docker run -d -p 8080:80 nginx (use any available host port:container ports, in my case I used the one mention earlier)

To make connection to the nginx container do the following: go to web browser, type localhost:8080, and you should see a welcome to nginx web page. Now you are able to connect to the application inside the container using the external port of your computer(i.e the host). The nginx html web page is located inside the container

Stop the container type: docker stop "container id/name
Remove the container: docker rm "container id/name"
