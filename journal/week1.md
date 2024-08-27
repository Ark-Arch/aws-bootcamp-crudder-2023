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

- docker run --rm -p 4567:4567 -it backend-flask FRONTEND_URL
    the -e helps to set environment variables in the container after it is run
    also the --rm would automatically remove the container after it has being stopped.
    without the --rm, the container would enter into an exited state. it would not be seen by 'docker ps', but by 'docker ps -a'

- docker compose up (docker-compose up)
    this is used to start and run Docker containers based on the services defined in a docker-compose.yml file.
    It would:
    - read the configuration file
    - build the images (if necessary)
    - create the containers
    - start the containers (backgroud/detached mode, or foreground/interactive mode)
    - creates and configures networks
    - creates and mounts volumes. - this would allow container to persist data and share files.
    * data persistence simply means that the data is stored in a named volume even after the contianer is stopped or removed. (docker volume ls)

***********************************************************
it is important to note that while trying to run a docker image, the name of the docker image should be at the last end of the command EXCEPT there is an intention to override it - by it, i mean the container!
***********************************************************
the difference between RUN and CMD commands in docker
- RUN is a command that we actually run to create a layer in the docker image. 
- CMD is the command the container would run when it starts up.

************************************************************
*container orchestration is the automated manaement of containerised applications. It is concerned with the managment of their deployment, scaling and monitoring.
- it helps to abstract underlying infrastructure, and provide a unified API for managing applications accross different environments.
CONTAINER ORCHESTRATION - docker-compose.yml
-> docker compose is a tool that allows you to define and manage multi-container Docker applications using a simple YAML file called 'docker-compose.yml'
- it is designed for applications that involve multiple services that need to run together.

Key Concepts in Docker Compose:
1. Service: this represents a single container. 
    in a docker-compose.yml file, you define multiple services that make up my application
2. Container:
    the running instance of a service
3. Network:
    Docker Compose automatically creates network between containers so they can communicate
4. Volumes:
    Persistent storage that can be shared between containers and survive container restarts.

*With docker compose, i can start my application with one command.

Although docker compose and kubernetes both deal with container orchestration, they are designed primarily for local development and testing environments, and not for production-level deployments. 

***********************************************************
networks:   # this is the top-level section where the custom networks are defined
  internal-network: # this is the name i am giving to the network. it is an identifier i can use within the compose file to specify which network my containers should connect to.
    driver: bridge
        # the driver specifies the type of network i want to create
        # the bridge is the default network driver in Docker.
            -> It is used to create an isolated network for my containers on a single host.
            -> Containers in a bridge network can communicate with each other by default, but they are isolated from external networks unless explicitly configured (like exposing ports).
            -> Using a bridge network is common for typical container networking scenarios where i want containers to communicate with each other while being isolated from the host or other external networks.
    name: cruddur # this is used to ensure the name of the network.

the above in the docker-compose.yml file is used to define a custom network configuration.
**************************************************************
advice
when starting a project, do it in two stages
1. write the Dockerfile ready to go, and make convenient shell scripts that would build, run etc. this would be my go to structure for any docker image
2. then have the docker-compose.yml file to run the image.
    let it be your goto for prototyping apps.
        start it from compose, and build it up in parrallel.

the difference between docker-compose up AND docker compose up

docker executable
docker-compose is a binary file

using docker-compose is running the docker-compose executable directly

**********************************************************
*service objects
- a concept that pushes the idea of breaking up code into concrete services

**************************************************************
SECURITY PRACTICES!!!!!!!!
top ten (10) container security practices
i can use while working as a cloud engineer, and a cloud security engineer.

Container Security is simply the practice of protecting your applications hosted on compute services like Containers.
Common examples of applications can be: 
1. Single Page Applications (SPAs)
    web applications that operate within a single web page.
    they load all the necessary resources required for the application in a single load.
    example is GMAIL; TWITTER; NETFLIX
    *React is for example used to build SPAs
    rather than loading entire new pages from the server in response to user actions, they just dynamically write the current page, allowing for a more fluid and responsive user experience.
    - SPAs serve a single HTML page to the browser and update the content dynamically, avoiding full page reloads.
    - they only load the necessary parts of the page on the user's requests.

    ADVANTAGLES
    - reduced server load.
    - improved user experience
    DISADVANTAGES
    - initial load time
    - a bit complex to build.

    SPAs are largely client-side applications.

SPAs are suitable for containerization because their architecture aligns well with the principles of lightweight, stateless, and portable environments that containers provide.

This therefore makes deployment , scaling and management more efficient and flexible.

2. Microservices
3. APIs

WHY CONTAINER SECURITY IS IMPORTANT?
1) containerization is cloud-agnostic. it is not tied to a cloud.
    there exists a container first strategy everywhere
    aws ecs
2) most applications are being developed with containers and are cloud native
3) it reduces the impact of breach - segragation of application(s) and related services.
4) 








