In this project I created a python code which is located on my local computer. The code asks to insert any positive integers, and sums all the integers from 0 to the given number, and gives you the outcome. To run this code a custom image (python app) was built on top of a python base image called Alpine.

Make sure you CD in 2.python-app folder then run the command using visual studio code.

Pull the latest python Alpine image from docker hub. Then you can map the local python file as volume mapping to the container. The command as follows:

**docker run -it -v ${PWD}:/app python:alpine python /app/main.py**

This command creates an image based on python:alpine, maping the volume to 2.python-app folder. Once the python code has been run then the container is exited. 

Dont forget to stop and remove the container and image after the task is completed

**docker stop "name of container**
**docker rm "name of image**
