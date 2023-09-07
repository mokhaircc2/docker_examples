In this project I created a python code which is located on local computer. To run the code it has to be  and want to run it with docker conatiner. So to run the code I used python:alpine

Make sure you CD in 2.python-app folder then run the command using visual studio code.

Pull the latest python image from docker hub. Then you can map the local python file as volume mapping to the container, this way the container will use the python code from local computer and run it. The command will be as follows using the python alpine image:

**docker run -it -v ${PWD}:/app python:alpine python /app/main.py**

This command creates an image based on python:alpine, maping the volume to 2.python-app folder 

Dont forget to stop and remove the container and image after the task is completed
