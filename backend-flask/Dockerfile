FROM python:3.10-slim-buster

########################   NOTES   ##########################
# the above line loads another docker file (the python docker file)
# this docker file can be found in the docker registry - docker hub
# FROM scratch -> an official docker image (an official empty image)
# it is a ground zero

# consider the below

# FROM scratch
# ADD rootfs.tar.xz
# CMD ["bash"]

# scratch is an official empty image. 
# the scratch is a 'no-op' -> no operations, being ignored.
# it is the second command that then adds the minimum root file system.

# EACH COMMAND IN A DOCKER FILE ESSENTIALLY CREATES A LAYER
# SO WHAT I END UP WITH IS A DOCKER IMAGE WHICH COMPRISES OF LAYERS

# CREATING A DOCKER IMAGE IS ACTUALLY CREATING LAYERS.

# Containers make use of a UNION FILE SYSTEM - one merged layer.


WORKDIR /backend-flask
# you should note that this directory been directed to is that on the guest OS inside the container.
# it does not respond to the /backend-flask in the host OS.

# since the file contains the libraries we need to run the app
# THIS COPIES FROM OUTSIDE TO THE INSIDE CONTAINER.
COPY requirements.txt requirements.txt

# install python variables
RUN pip3 install -r requirements.txt
# the RUN command is used to run a layer command as part of the docker image.

COPY . .

# set the Env Vars. and will remain set when the container is running.
ENV FLASK_ENV=development

EXPOSE ${PORT}
# the above expose command i think is meaningless since the PORT variable is not set.

# this command is what runs the flask application.
CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0", "--port=4567"]
#python3 -m flask run --host=0.0.0.0 --port=4567

# the '-m' this hyphen-m says to run the flask module
# in practicality, it is important to bind it to the host=0.0.0.0. when dealing with containers!
