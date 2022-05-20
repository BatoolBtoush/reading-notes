# **Readings: Django REST Framework & Docker**


## **Docker:**

Docker is a containerization platform that provides a container runtime environment for applications. It is a software stack that enables developers to run applications on a containerized virtual machine.

The entire development environment is isolated: programming language, software packages, databases, and more. With Docker we now longer have to mess around with virtual environments. We can faithfully reproduce a production environment locally. And Docker can be shared among team members so everyone is working on the same setup. Wins all around.

<br>

### **What is a container?**

A container is a virtual machine that runs on top of a Linux operating system. It is a lightweight, portable, and isolated environment. It is a containerized version of a Linux operating system. 


### **Container's characteristics:**
- is a runnable instance of an image. You can create, start, stop, move, or delete a container using the DockerAPI or CLI.
- can be run on local machines, virtual machines or deployed to the cloud.
- is portable (can be run on any OS)
- Containers are isolated from each other and run their own software, binaries, and configurations.

taken from: [docker docs: What is a Container ](https://docs.docker.com/get-started/#what-is-a-container)

<br>

### **Containers vs Virtual Environments**

**Virtual environments** are used to isolate Python software packages locally. We can create an isolated box for individual projects so one can use Python 2.7 and Django 1.5 while another can use Python 3.5 and Django 2.1 on the same computer. Virtual environments are great.

But…virtual environments can only isolate Python packages. They still rely on a global, system-level installation of Python albeit they can refer to the proper version. So when we use Python 2.7 in a project, we’re pointing to an installation of Python 2.7 on the computer itself, not actually within the virtual environment.

Also we can’t run a production database or other services within virtual environments so compared to Docker containers they are far more limited.


<br>

### **Install Docker**

1. To install Docker we need to download the desktop app on our computer and create a free account. 

2. Once Docker is done installing we can confirm the correct version is running. It should be at least version 19.

    ```
    $ docker --version
    Docker version 19.03.5, build 633a0ea
    ```

3. Now run the command below to confirm you have a working version of Docker Compose, too. The version should be at least 1.24.x.
    ```
    $ docker-compose --version
    docker-compose version 1.24.1, build 4667896b
    ```

4. To confirm Docker installed correctly we can run the command ```docker run hello-world```. This will download an official image and then run the container. 
    ```
    $ docker run hello-world
    Unable to find image 'hello-world:latest' locally
    latest: Pulling from library/hello-world
    1b930d010525: Pull complete
    Digest: sha256:9572f7cdcee8591948c2963463447a53466950b3fc15a247fcad1917ca215a2f
    Status: Downloaded newer image for hello-world:latest

    Hello from Docker!
    This message shows that your installation appears to be working correctly.

    To generate this message, Docker took the following steps:
    1. The Docker client contacted the Docker daemon.
    2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
        (amd64)
    3. The Docker daemon created a new container from that image which runs the
        executable that produces the output you are currently reading.
    4. The Docker daemon streamed that output to the Docker client, which sent it
        to your terminal.

    To try something more ambitious, you can run an Ubuntu container with:
    $ docker run -it ubuntu bash

    Share images, automate workflows, and more with a free Docker ID:
    https://hub.docker.com/

    For more examples and ideas, visit:
    https://docs.docker.com/get-started/
    ```

<br>

### **Images and Containers**

Images and containers are the two fundamental concepts to grasp when you start with Docker. An image is a snapshot in time of what a project contains. A container is a running instance of the image.

When we ran hello-world we used an official Docker image. We did not have to create the image ourself. But typically we will create custom images and we do so using a Dockerfile.

<br>


## **Django REST Framework**

Django REST Framework works alongside the Django web framework to create web APIs. We cannot build a web API with only Django Rest Framework. It always must be added to a project after Django itself has been installed and configured.


### **Traditional Django and Django REST Framework**

Django creates websites containing webpages, while Django REST Framework creates web APIs which are a collection of URL endpoints containing available HTTP verbs that return JSON.

