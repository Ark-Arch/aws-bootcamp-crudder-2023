# Week 1 — App Containerization

*I just learnt about CORS

Cross-Origin Resource Sharing (An API security practice)
- this is a security feature implemented by web browsers to prevent malicious websites from making unauthorized requests to another site.

- it restricts how resources on a web page can be requested from another domain.

- By default, web applications are limited to interacting with resources from the same origin (same domain, protocol, and port).
-> So when my application serves an API that should be accessible from different domains, CORS is needed.


flask-cors is python extension for handling Cross-Origin Resource Sharing in Flask applications.

key-words with CORS
- origin requests.
-> the solution to a CORS error is on the server. i have to be able to control the server
- that is how i can include headers (or preflight the headers)

***********************************************************
DOCKER COMMAND LINE PROMPTS I HAVE LEARNT.
- docker build -t backend-flask:1.0.0 ./backend-flask
    this would build a docker image from the docker file available

- docker images 
    this would list the docker images available

- docker run --rm -p 4567:4567 -it backend-flask:1.0.0
    this would create a new container
    and would then run a command in it
    -p maps the host's port to a container's port

- docker ps 
    this would list the running docker containers

- docker exec
    this runs a command inside an existing, running container
    examples:
    docker exec container_name_or_id python /app/my_script.py
        this would run a python script located at /app/my_script.py inside the container
    docker exec -it container_name_or_id bash
        THIS TAKES ME INTO THE CONTAINER ITSELF!
        this would run the bash command inside the container
        the -it allows the STDIN stream open (-i) which allows me to provide input interactively; and -t allocates a pseudo-terminal, which would provide an interactive shell experience (like i would have with SSH)
        so -it allows me to interact with the container as if i am inside a typical terminal session.

- docker rmi container_name_or_id
    this would remove docker images
***********************************************************
the difference between RUN and CMD commands in docker
- RUN is a command that we actually run to create a layer in the docker image. 
- CMD is the command the container would run when it starts up.