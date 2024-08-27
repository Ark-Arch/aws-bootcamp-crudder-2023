Difference between RUN CMD and ENTRYPOINT

the RUN command is used to provide commands that adds a layer to the image during build process.
    it is typically used for necessary installations that would be needed by the container to run the process

the CMD command is used to provide a command that runs by default when the docker container is run.
    it typically consists of an executable.
    but it is easily overriden during the 'docker run' command.
    e.g docker run <CONTAINER> echo "i have overriden it". echo executable overrides the CMD command.
    CMD ["executable", "param1", "param2"]

the ENTRYPOINT command is more rigid. 
    it typically describes the executable that should be run after the docker run command is executed on the container
    the CMD command usually just contains the arguments of the executable in the entry point.

    e.g 
    ENTRYPOINT ["python", "app.py"]
    CMD ["--help"]

