# DockerTutorial

Learning Docker using "Docker Tutorial for Beginners"

## What is Docker

    - Platform for building, running and shipping applications
    - Docker can package applications and run it anywhere
    - Docker will run everything within an isolated container
    - Allows mulitple applications with different versions, without conflict
    - We can safely removed dependencies without fear of the application breaking

## Virtual Machines vs Container

    - VM: An abstraction of a machine (physical hardware)
    - Container: An isolated environment for running an application

## VM

    - Example we can use a "hypervisor" to run both windows and linux, hypervisors is software to create and manage virtual machines,e.g. VirtualBox, VMware, Hyper-v(Windows only)
    - for developers we can run two virtual machines and have different software versions on both and use the exact same dependencies.
    - problems: Each VM needs a full blown OS, slow to start, resource intensive

## Containers

    - Allow running multiple apps in isolation
    - Are lightweight
    - Use OS of the host
    - Start Quickly
    - Needs less hardware resources

## How Docker Works?

    - Client talks to server using REST API
    - Server is called Docker Engine, takes care of building and running
    - Containers share the OS of the host (more specificaly the kernel)
    - Each kernel has its own OS, The kernel manages application and hardware resources
    - These kernels have different API's, because of this they can only use the OS shipped with the type of OS
    - Windows can use both (windows and linux), as it is shipped with both
    - Linux can only use (linux)
    - macOS, has its own kernel, no native support. Docker using a lightweight linux VM to run linux containers.

## Docker Architecture

    - containers are just like other proccesses running on your computer

## Docker Workflow

    - With our application to Dockerize it we need to add a Docker File to it
    - Dockerfile is a text file that pcakages everything up into an image
    - image contains everything we need to run the application
        *   Things such as a cut-down OS, runtime env (e.g. node), app files, third party
        libraries, env variables
    - Once we have an image we ask Docker to start up container using that image.
    - Application is loaded locally on our machine using the docker container
    - instead of running the project locally using "app run dev" for example, we use
    "docker run ..."
    - once we have the docker image we can send it to a registry such as docker hub, we can then put it on any machines running docker, kind do like github.

## how to run Docker

    - Complete Docker file,
    - FROM node:alpine (or any source app e.g. ubuntu)
    - COPY . /app
    - WORKDIR /app
    - CMD node app.js

    - Tell docker to package in terminal
    - ```docker build -t hello-docker .```
    - we have to specify tag name for th image being hello-docker
    - we have to specify where cocker can find the file so we use
    - a . to specify the current location it is in.
    - ```docker image ls``` shows us the docker images
    - can execute using command ```docker run hello-docker```

## dockerhub

    - When trying to push an image to a version control hub like dockerhub.
    - you need to first tag it:
    - ```docker tag $local-image:$tagname $new-repo:$tagname```
    - ```docker push new-repo:tagname```
    - in my case I used the command ```docker tag hello-docker albert203/dockertutorial```, note that on dockerhub my namespace is called albert203 and my repo name is called dockertutorial.
    - finally to push you use the command ```docker push $repository```
    - in my case I ran the command ```docker push albert203/dockertutorial```
    - URL to image, [dockerrepo](https://hub.docker.com/repository/docker/albert203/dockertutorial/general)
