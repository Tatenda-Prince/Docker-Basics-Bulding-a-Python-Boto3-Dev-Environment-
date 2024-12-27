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

In the Windows 11 WSL Linux command line, check if docker is already installed by running the following commands —

docker version

If it is already installed, you should see a similar output in you CLI with the client and server and their installed versions.

![image alt]()

Now verify that Docker is running by running the following command —

docker info


If Docker is running, you should see the “1” next to “Running” in the output.

![image alt]()













