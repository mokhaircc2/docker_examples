In this project I created a container based on custom image

Make sure your in the 3.python-custom folder using the visual studio code to run commands

Run the following command:

docker build . -t python-custom

docker run -it python-custom sh
once inside the container you can type ls to see that the dokerfile and main.py file are listed

