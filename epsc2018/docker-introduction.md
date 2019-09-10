# Docker with Mario at OpenPlanetaryDataCafe - EPSC2018

- What is Docker?
- Different from VirtualBox: it's more single app-oriented.

- Docker "dialect" : To use a programming metaphor, if an image is a class, then a container is an instance of a class—a runtime object. Containers are hopefully why you're using Docker; they're lightweight and portable encapsulations of an environment in which to run applications.

- Example: docker with python + jupyter, a web server.

- Docker works differently in GNU/Linux vs Win|Mac : it is native on Linux ,  Win|Mac use an hidden Virtual machine hypervisor hidden to the user.

- User interface: command line `docker [command] [option] [image name]`

- You normally start a virtual machine with a root account

### Basic commands

- `docker search` search image repository
- `docker pull [image name]` -> search image repository
- `docker ps` : see running container
- `docker run [options] [image name]` : run a container from an image
  - Options: 
  - `-v| --volume  HOST_DIRECTORY_PATH:CONTAINER_DIRECTORY_PATH` : mount your local HOST_DIRECTORY_PATH to CONTAINER_DIRECTORY_PATH in the container. It the latter exists, it will be overwritten. Useful to share configuration or state files forth and back from the container.
  - `-p|--publish 80:81 ` : Publish a container's port(s) to the host, in this case if you ask something the port 81 to the host it will be redirect to the 80 in the container.
  -  `-i, --interactive` : Keep STDIN open even if not attached
  - `-t|--tty`: Allocate a pseudo-TTY

### Example 

```sh
docker run -i -t --rm debian:9
```
This run docker images degian tag 9, keep STDIN open, allocate a pseudo-TTY  and remove on exit.

### Process example from scratch

1. you install docker 
2. you search the docker images
3. there are official images - like ubuntu.  Using the official ones is safer for a newbie.
4. Search by tags facilitates
5. we did a docker pull debian
6. what images do I have locally?: docker images
7. docker run -i debian
8. you can run GUI application like (you need xeys installed in the image, see below and use the appropriate command for mac/win host): 
    - `docker run -e DISPLAY=docker.for.mac.localhost:0 -v /tmp/.X11-unix:/tmp/.X11-unix debian:9-xeyes /usr/bin/xeyes` 
    - `docker run -e DISPLAY=docker.for.win.localhost:0 -v /tmp/.X11-unix:/tmp/.X11-unix debian:9-xeyes /usr/bin/xeyes` 
9. aliasing bash command to docker: `alias dockerls="docker run -ti --rm -v $(pwd):/data debian /bin/ls"` this run a container on the fly, pass the local directory to /data in the container, and pass also option to the option the internal command.


If we want to build our image.  We have to prepare a configuration file called Dockerfile. 

Here a minimal example for the point 8 above. Create a file named [Dockerfile](https://docs.docker.com/engine/reference/builder/)

```
FROM debian:9
RUN apt-get update
RUN apt-get install -qqy x11-apps
CMD ["/usr/bin/xeyes"]
```

build the image with docker:

```
# name: debian, tag: 9-xeyes, . : search local directory
docker build -t debian:9-xeyes . 
```

Now you have a container `debian:9-xeyes` locally.

### Further Reading 

- [docker commit | Docker Documentation](https://docs.docker.com/engine/reference/commandline/commit/)

### Experiment

Docker debian on MS Windows 10 machine
