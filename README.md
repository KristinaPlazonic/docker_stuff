# Docker TLDR

```
docker build -t friendlyhello .  # Create image using this directory's Dockerfile
docker run -p 4000:80 friendlyhello  # Run "friendlyname" mapping port 4000 to 80
docker run -d -p 4000:80 friendlyhello         # Same thing, but in detached mode
docker container ls                                # List all running containers
docker container ls -a             # List all containers, even those not running
docker container stop <hash>           # Gracefully stop the specified container
docker container kill <hash>         # Force shutdown of the specified container
docker container rm <hash>        # Remove specified container from this machine
docker container rm $(docker container ls -a -q)         # Remove all containers
docker image ls -a                             # List all images on this machine
docker image rm <image id>            # Remove specified image from this machine
docker image rm $(docker image ls -a -q)   # Remove all images from this machine
docker login             # Log in this CLI session using your Docker credentials
docker tag <image> username/repository:tag  # Tag <image> for upload to registry
docker push username/repository:tag            # Upload tagged image to registry
docker run username/repository:tag                   # Run image from a registry
```
from: https://docs.docker.com/get-started/part2/#recap-and-cheat-sheet-optional

# Singularity TLDR

```
singularity shell docker://ubuntu:latest
singularity run docker://ubuntu:latest
singularity exec docker://ubuntu:latest echo "Hello Dinosaur!"
singularity pull docker://ubuntu:latest
singularity build ubuntu.img docker://ubuntu:latest
```
from: https://www.sylabs.io/guides/2.6/user-guide/singularity_and_docker.html

# Introduction

# Exersices 0: 

- follow these commands and find out what they are doing by executing `docker ps` (which gives you the list of running containers) after each command (or `docker ps -a` to give all)
```
docker run -dt busybox   # runs busybox in detached mode 
docker run -t myfirstcontainer busybox  #exits right away
docker run --name myfirstcontainer -d busybox  #exits right away
docker run --name myfirstcontainer2 -dt busybox #keeps running because it's detached from the shell 
docker stop myfirstcontainer2
docker rm myfirstcontainer2
docker run -itd keeprunning busybox
docker exec keeprunning pwd   # will give root, because you are inside the container now
docker exec keeprunning sh -c "pwd && ls && echo blah"  # busybox doesn't have bash, only sh; here we want 3 commands to execute *inside* the container
docker image ls # list all images
```

# Exercise 1:
1. pull busybox:latest docker image (find it in https://hub.docker.com/explore/ and pull to your laptop)
2. start the container from this image
3. execute `echo hello world!` from this container

# Exercise 2: 
1. start with a docker ubuntu image (find it in https://hub.docker.com/explore/ and pull to your laptop) 
2. install R in the image to create a new docker image; 
3. add an R script inside the image
3. Start a container from the image
3. then run hello world in R from that container  (i.e. run the following command `Rscript hello_world.R`)
4. then do the same but run with singularity

# Exercise 3: 
1. start with a docker ubuntu image (find it in https://hub.docker.com/explore/ and pull to your laptop)
2. install R in the image to create a new docker image;
3. Install an R library inside the image (library `caret` that's a goto library for machine learning in R)
4. Having a given program that trains a simple machine learning model on iris data, run a singularity container that trains this model on this data on Amarel. 
(example of plotting and training models: https://machinelearningmastery.com/machine-learning-in-r-step-by-step/)

# Exercise 4: 

Repeat exercise 4 with a base image given by https://github.com/nickjer/singularity-rstudio/blob/master/Singularity, but instead of 3, install a list of packages listed in a textfile. 
