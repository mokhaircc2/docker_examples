#pulls the base image of python alpine from docker hub
FROM python:alpine

# set the working directory as app
WORKDIR /app

# run and install the requirments and dependencies
RUN pip install pymongo

# copy the app file and the dependencies into the working directory
COPY . /app

# run the main.py file
CMD [ "python",  "main.py" ]
