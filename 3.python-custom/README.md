In this project I created custom image using docker file, one for running Python application and the other mongodb. Containers were created from these images. The containers were attcahed to each other using custom bridge network which allowed communication with each other using the names of the container. Here two seperate docker run commands were used to run the containers, first one for mongodb and the the second run command for python app.

Make sure your in the 3.python-custom folder using the visual studio code to run commands

Run the following command:

docker build . -t python-custom

docker run -it python-custom sh
once inside the container you can type ls to see that the dokerfile and main.py file are listed. Exit the shell then the container, control c, then type exit

