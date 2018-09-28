# Docker TLDR

- TODO 

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
