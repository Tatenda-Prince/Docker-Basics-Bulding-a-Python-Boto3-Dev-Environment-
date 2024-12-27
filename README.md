# Docker-Basics-Bulding-a-Python-Boto3-Dev-Environment-
"Lets Dock this Boat"

![image alt](https://github.com/Tatenda-Prince/Docker-Basics-Bulding-a-Python-Boto3-Dev-Environment-/blob/d3273d3cd5ee5c602193e383042eb26702dc7eeb/images/Screenshot%202024-12-27%20111744.png)

# Intro

Imagine building your dream house. You start by laying the foundation, then adding walls, wiring, plumbing, and all the other essential components. Once everything is complete, you have the house of your dreams, ready to live in and enjoy.

Now, suppose you decide to move this house to a different location. This would be a challenging and costly endeavor because you’d need to dismantle the entire structure, transport all the pieces, and then painstakingly reassemble them at the new site. Wouldn't it be so much easier if you could simply pick up the entire house and relocate it in one seamless move?


This is where Docker comes in. Docker is like a special container that you can put your house into. Instead of taking the house apart and moving all the pieces, you can just pick up the container and move it to the new location. Everything that’s inside the container, including the foundation, walls, wiring, plumbing and everything else, stays together and works just the same as it did before.

In software development terms, Docker is a platform that allows developers to package up their applications and all the necessary components, like libraries and dependencies, into a single container. This makes it easy to move the application from one environment to another, like from a developer’s laptop to a testing server or from a testing server to a production server.

Just like how a house can be put into a container for easy moving, software applications can be packaged into Docker containers for easy deployment and portability across different computing environments.


Today, I’m going to take you through some of Docker’s fundamental commands and concepts by creating a Python/Boto3 development environment involving building a custom image, running containers and creating bind mounts to repos.

# Docker Information

# Docker image

A Docker image is a packaged template that defines how a container is to be created which can run on the Docker platform.

# Dockerfile

A Dockerfile is a text document in which you are able to include commands that describe steps to assemble an image.

# Docker pull

The docker pull command enables you to pull container images from the internet.

# Docker run 

The docker run command enable you run a desired container which is layered over a Docker image and gives you ability to run commands inside it.

# Docker ps

The docker ps shows both the running and stopped container.

# Bind mount

A bind mount allows you to mount a file or directory on the host machine into a container.

# Prerequisites

Basic knowledge and understanding of containerization and Docker

Basic Linux command line knowledge

AWS Account with an IAM User

Basic knowledge and use of the AWS Cloud9 Interactive Development Environment (IDE)

# Objectives

With a Dockerfile, build an Ubuntu image for Python/Boto3

Download any three repos to local host

Run three Python/Boto3 containers and bind mount each to one of the repos

Log into each container and verify access to each repo directory

# Step 0: Setting up Docker Environment

In the Windows 11 WSL2  Linux command line, check if docker is already installed by running the following commands —

docker version

If it is already installed, you should see a similar output in you CLI with the client and server and their installed versions.

![image alt](https://github.com/Tatenda-Prince/Docker-Basics-Bulding-a-Python-Boto3-Dev-Environment-/blob/50ad0e35b112ea23abf2c52c377459d74bb6ad18/images/Screenshot%202024-12-27%20114357.png)


Now verify that Docker is running by running the following command —

docker info


If Docker is running, you should see the “1” next to “Running” in the output.

![image alt](https://github.com/Tatenda-Prince/Docker-Basics-Bulding-a-Python-Boto3-Dev-Environment-/blob/c66b2ab840dee84a652731f2f0d9cf00bb2b78c0/images/Screenshot%202024-12-27%20114438.png)


# Step 1: Build image with Dockerfile for Python/Boto3

Head to the dockerhub and locate the Docker official Ubuntu image, along with the desired tag.

We will use the latest Ubuntu tag “22.04”.

![image alt](https://github.com/Tatenda-Prince/Docker-Basics-Bulding-a-Python-Boto3-Dev-Environment-/blob/def7caa088839be7ce0f63c10077b9bde4afeee0/images/Screenshot%202024-12-26%20193209.png)


Now head to your Windows 11 WSL2 Linux , create a directory to store all files, then navigate into the directory.


![image alt](https://github.com/Tatenda-Prince/Docker-Basics-Bulding-a-Python-Boto3-Dev-Environment-/blob/d26c0075eaf613f24d2e4450fbabd1f32e833a16/images/Screenshot%202024-12-26%20193437.png) 

We can now create a Dockerfile which will be used to build our Python/Boto3 image by running the following command —

nano Dockerfile

A text editor window should open to edit our Dockerfile. Copy and paste the code below into the text editor.

FROM ubuntu:22.04

RUN apt-get update

RUN apt-get -y install python3-pip \
    && pip install boto3

Let’s break down what each line is doing —
The first line of the Dockerfile builds a custom image from “ubuntu:22.04”. The second and third line run two separate commands. The first updates the current packages and the second installs Python/Boto3 on the image.

Proceed by typing the “Ctrl and O” key together to save the file, then press Enter. Type “Ctrl and X” to exit the text editor.


We now need to build the image using this Dockerfile. To build the image, run the following command —

Don’t forget to add the “.” at the end of the command to use the Dockerfile in the current directory.

docker image build -t <custom_name_for_image> .

The image will begin to build based on the configurations in the Dockerfile. Wait a few seconds until it is completed.


![image alt](https://github.com/Tatenda-Prince/Docker-Basics-Bulding-a-Python-Boto3-Dev-Environment-/blob/b417e370048af8cc77798ea9f2319ac7008cb128/images/Screenshot%202024-12-26%20194505.png)


Once completed, we can list the images in our local system by running the following command —

docker image ls


There should be a image, the “python_boto3” images downloaded from Dockerhub which was used to build the custom image from our Dockerfile configurations.

![image alt]()


















