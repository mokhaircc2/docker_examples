In this project I created custom image using docker file, one for running Python application and the other mongodb. Containers were created from these images. The containers were attcahed to each other using custom bridge network which allowed communication with each other using the names of the container. Here two seperate docker run commands were used to run the containers, first one for mongodb and the the second run command for python app. This method is not practical if you have many containers to run. In the next project I will use docker compose, where I can use one single command for running multiple containers simultaneously.

Make sure your in the 3.python-custom folder using the visual studio code to run commands

Run the following command:

docker build . -t python-custom (here instruction from docker file is requesting to use python:alpine image which is pulled from docker hub, -t flag is to tag the image and call it in this case python-custom). Next the docker file specified a working directory called /app. Next pip is installed inside pymongo i.e all dependencies. Next all application files from local folder on my computer is copied into ./app file inside the container). So on top of the base image (python:alpine) the build process adds 3 addition files system layers i.e workdir, run pip and copy . app. Now run the build:

docker run -it python-custom (this command times out and wont run the container, because the python application is not able to resolve the mongo name to its ip address)

docker run -it python-custom sh
once inside the container you can type ls to see that the dokerfile and main.py file are listed. Exit the shell then the container, control c, then type exit

now type docker run -d --name=mongo, to run mongodb container. After mongodb is running, re-try running the python-custom container:
docker run -it python-custom

the container times out again, because the python application is not able to resolve the mongo name to its ip address - you have to create a network bridge between the two containers. However the two containers can communicate with each other using their ip addresses, but not names)

Type docker network list, and you will see 3 networks - bridge, host and null.
Now to create custom bridge network do as follows:

docker network create "name of network", e.g "python-mongo"
Now type docker network list, and you will see the newly created network, python-mongo. Docker runs internal DNS server which resolves names and IDs f the containers to their ip addresses

Now attach the custom bridge network to the running container (mongo container is the running container):
docker network connect python-mongo mongo

Now run the python-custom container which will run the python application:
docker run -it --network=python-mongo python-custom
after this is executed you will see an output, which is a list of databases from mongodb and then the python container will be exited because running of python application was successful.
