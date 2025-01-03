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

1.Basic knowledge and understanding of containerization and Docker

2.Basic Linux command line knowledge

3.AWS Account with an IAM User

# Objectives

1.With a Dockerfile, build an Ubuntu image for Python/Boto3

2.Download any three repos to local host

3.Run three Python/Boto3 containers and bind mount each to one of the repos

4.Log into each container and verify access to each repo directory

# Step 0: Setting up Docker Environment

In the Windows 11 WSL2  Linux command line, check if docker is already installed by running the following commands —

~ docker version

If it is already installed, you should see a similar output in you CLI with the client and server and their installed versions.

![image alt](https://github.com/Tatenda-Prince/Docker-Basics-Bulding-a-Python-Boto3-Dev-Environment-/blob/50ad0e35b112ea23abf2c52c377459d74bb6ad18/images/Screenshot%202024-12-27%20114357.png)


Now verify that Docker is running by running the following command —

~ docker info


If Docker is running, you should see the “1” next to “Running” in the output.

![image alt](https://github.com/Tatenda-Prince/Docker-Basics-Bulding-a-Python-Boto3-Dev-Environment-/blob/c66b2ab840dee84a652731f2f0d9cf00bb2b78c0/images/Screenshot%202024-12-27%20114438.png)


# Step 1: Build image with Dockerfile for Python/Boto3

Head to the dockerhub and locate the Docker official Ubuntu image, along with the desired tag.

We will use the latest Ubuntu tag “22.04”.

![image alt](https://github.com/Tatenda-Prince/Docker-Basics-Bulding-a-Python-Boto3-Dev-Environment-/blob/def7caa088839be7ce0f63c10077b9bde4afeee0/images/Screenshot%202024-12-26%20193209.png)


Now head to your Windows 11 WSL2 Linux , create a directory to store all files, then navigate into the directory.


![image alt](https://github.com/Tatenda-Prince/Docker-Basics-Bulding-a-Python-Boto3-Dev-Environment-/blob/d26c0075eaf613f24d2e4450fbabd1f32e833a16/images/Screenshot%202024-12-26%20193437.png) 

We can now create a Dockerfile which will be used to build our Python/Boto3 image by running the following command —

~ nano Dockerfile

A text editor window should open to edit our Dockerfile. Copy and paste the code below into the text editor:

} FROM ubuntu:22.04

RUN apt-get update

RUN apt-get -y install python3-pip \
    && pip install boto3
    {

Let’s break down what each line is doing —
The first line of the Dockerfile builds a custom image from “ubuntu:22.04”. The second and third line run two separate commands. The first updates the current packages and the second installs Python/Boto3 on the image.

Proceed by typing the “Ctrl and O” key together to save the file, then press Enter. Type “Ctrl and X” to exit the text editor.


We now need to build the image using this Dockerfile. To build the image, run the following command —

Don’t forget to add the “.” at the end of the command to use the Dockerfile in the current directory.

~ docker image build -t <custom_name_for_image> .

The image will begin to build based on the configurations in the Dockerfile. Wait a few seconds until it is completed.


![image alt](https://github.com/Tatenda-Prince/Docker-Basics-Bulding-a-Python-Boto3-Dev-Environment-/blob/b417e370048af8cc77798ea9f2319ac7008cb128/images/Screenshot%202024-12-26%20194505.png)


Once completed, we can list the images in our local system by running the following command —

~ docker image ls


There should be a image, the “python_boto3” images downloaded from Dockerhub which was used to build the custom image from our Dockerfile configurations.

![image alt](https://github.com/Tatenda-Prince/Docker-Basics-Bulding-a-Python-Boto3-Dev-Environment-/blob/13863b6dab9bcb90bc0cdcda439c8ee371eb4791/images/Screenshot%202024-12-26%20194513.png)

Now that the Python/Boto3 image has been built, we can proceed to Step2 — Downloading three repos to your local system.


# Step 2: Download three repos to local system

In your Windows 11 WSL2 Linux , clone any three repos from the internet into our local system in the directory of the Dockerfile. You can choose which ever three you desire.

Run the following three commands to clone these random three public GitHub repos —

git clone https://github.com/ifeanyiro9/python_LUIT.git

git clone https://github.com/KinzP/eks-cluster-terraform.git

git clone https://github.com/KinzP/cicd_terraform.git

![image alt](https://github.com/Tatenda-Prince/Docker-Basics-Bulding-a-Python-Boto3-Dev-Environment-/blob/21ed875e82c886a273cd5371aaf3d7707ef45bbb/images/Screenshot%202024-12-26%20195315.png)


If you run the “ls” command, you will see all three repo directories created on your local system.

![image alt](https://github.com/Tatenda-Prince/Docker-Basics-Bulding-a-Python-Boto3-Dev-Environment-/blob/fb333744f87e5d983b713d43ff725da2c2dec3b0/images/Screenshot%202024-12-26%20195347.png)


Now, lets proceed to Step 3: creating three containers from our Python/Boto3 image.


# Step 3: Run three Python/Boto3 containers and bind mount each to a repo

To bind mount a container, we will use the flag “-v”. This enables us to mount a file or directory on the host machine into a container.

The following command runs a container with the custom given name “boto3_cicd” from the “python_boto3” image built previously.

It uses the “-d” flag to run detached in the background and the “-t” flag which allocates a virtual terminal session within the container to keep the container running.

The “-v” flag bind mounts the “cicd_terraform” repo directory to the “applications” directory in the container.

Run the commands for all three of the repo directories and name the containers to match the directories they will be mounted to.

cici_terraform repo bind mount —

docker run -d -t --name boto3_cicd -v /home/ec2-user/environment/boto3_dev/cicd_terraform:/cicd_terraform python_boto3 

python_LUIT repo bind mount —

docker run -d -t --name boto3_pl -v /home/ec2-user/environment/boto3_dev/python_LUIT:/python_LUIT python_boto3

eks-cluster-terraform repo bind mount —

docker run -d -t --name boto3_ect -v /home/ec2-user/environment/boto3_dev/eks-cluster-terraform:/eks-cluster-terraform python_boto3

List all the containers we’ve created by running the following command —

~ docker ps

You should be able to see all three containers running.

![image alt](https://github.com/Tatenda-Prince/Docker-Basics-Bulding-a-Python-Boto3-Dev-Environment-/blob/487d749ce9a9060bb89f5d197ebea76d60e648fc/images/Screenshot%202024-12-26%20200023.png)


Now that we’ve created our containers, and a bind mount to our repo directories for each, let’s proceed to Step 4: Verifying access to each repo directory from each container.


# Step 4: Login to containers and verify access to repo directory

Terminal 1 — boto3_cicd

docker exec -it boto3_cicd bash

Terminal 2 — boto3_pl

docker exec -it boto3_pl bash

Terminal 3 — boto3_ect

docker exec -it boto3_ect bash


If you list all the directories and files in each container in each terminal by running the “ls” command, you should be able to see the repo directory.

Navigate into the repo directories by running “cd” command, then list the directories contents again.

You should be able to view and verify all the files in and folders from the repo directory on you local system is now in your container.


cicd_terraform repo —

![image alt](https://github.com/Tatenda-Prince/Docker-Basics-Bulding-a-Python-Boto3-Dev-Environment-/blob/a106d6c10c622a75d2950468d96e00f9f28b612c/images/Screenshot%202024-12-26%20200636.png)


python_LUIT repo —

![image alt](https://github.com/Tatenda-Prince/Docker-Basics-Bulding-a-Python-Boto3-Dev-Environment-/blob/edee252122a9b25db7436476224aa0e32690eb7a/images/Screenshot%202024-12-26%20201047.png)


eks-cluster-terraform repo —

![image alt](https://github.com/Tatenda-Prince/Docker-Basics-Bulding-a-Python-Boto3-Dev-Environment-/blob/5cfe2a410c8fa97d30a805393f845675712428c1/images/Screenshot%202024-12-26%20201139.png)


# Success!
We have verified access to the repo directories from each container enabled by the bind mounts!

Further more, in your local system, create a new file “new_file.txt” in one of the repo directories, then head to its corresponding container.

You should be able to see change also reflected in the repos directory in the corresponding container.


![image alt](https://github.com/Tatenda-Prince/Docker-Basics-Bulding-a-Python-Boto3-Dev-Environment-/blob/1c4968ca64c6fe719883e9bd04f5acdda38dd080/images/Screenshot%202024-12-26%20201422.png)


Replicate this verification method with the other repo directories in your local system and their corresponding containers. Verify that you get the same results!

# Congratulations!
You’ve successfully “Docked this Boat”. You’ve learned Docker fundamentals commands and concepts by creating a Python/Boto3 development environment which involved building a custom image from a Dockerfile, running containers and creating bind mounts to repos on your local system.






















