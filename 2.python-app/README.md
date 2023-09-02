In this project we have a small python code on our local computer and want to run it with docker conatiner.

Pull the latest python image from docker hub. Then you can map the local python file as volume mapping to the container, this way the container will use the python code from local computer and run it. The command will be as follows:

docker run -it -v ${PWD}:/app python:alpine python /app/main.py
