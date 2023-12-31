Compose is a tool for defining and running multi-container Docker applications. With Compose, you use a YAML file to configure your application's services. Then, with a single command, you create and start all the services from your configuration.

Compose works in all environments; production, staging, development, testing, as well as CI workflows. It also has commands for managing the whole lifecycle of your application:

Start, stop, and rebuild services
View the status of running services
Stream the log output of running services
Run a one-off command on a service

In this project I will be using docker compose to build a python app image on top of a python base image and running a seperate mongodb container from the dockerhub. Once the python container runs the application the output is to list data from the MongoDB database. This project is almost the same as the previous 3.python-custom (which was to run each dockorfile separately). However the difference is that Docker compose file is a way to declaratively orchestrate the startup of multiple containers and therefore automatically creates images, runs containers and creates network bridges according to what is specified in the docker compose file with a simple command. Docker compose uses yaml language, so the spacing is crucial and must be either 2 spaces or 4 (not both) and don't use the tab key.

On the docker compose file there is a version number, which is the latest version of docker compose being used. The services tells us what we going to start and use. In this case two services/containers will be used, app and mongo. 


To run the docker compose file type:

**docker compose up**

here the building of the app service (i.e custom python-image) occurs and mongodb image is pulled from dockerhub, then containers are created as well as custom netowrk bridge, and finally the application is run on the container. Once the application is run and executed, it will stop the container running the process, in this case python-compose_app will stop running and python-compose-mongo will still be running. You can view the logs and see the output as list of databases as was specified in the main.py file.

To view which containers are running type

**docker ps -a**

Check the custom network bridge is created **docker network list**

press control c on terminal to stop both container

**docker compose down**, will stop and remove all running containers and custom network
