## Intro

This is my Udacity Cloud DevOps Capstone project. In this project I created a CI/CD pipeline for a basic website that deploys to a cluster in AWS EKS

## Install

To be able to use this CI/CD pipeline we will need:
- Jenkins
- eksctl
- aws cli
- docker
- kubectl

1. To install Jenkins please follow this guide http://jenkins.io/doc/book/installing/
2. To install docker please follow this guide https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04
3. To install eksctl, aws cli and kubectl follow this guide https://docs.aws.amazon.com/eks/latest/userguide/getting-started-eksctl.html

## Project tour

There are 3 pipelines. I am going to guide you on the pipelines and how are the use from the beginning to the moment that the application is deployed.

### 1. Create clusters pipeline

**Pipeline**

You can see this  pipeline in the image called **Pipelines diagram.png** in the "Pipeline 1". You can see the **Jenkinsfile** in the folder **create-clusters-pipelines**.

**Result**

In there you use the **eksctl** to create the **cluster for the blue system** and the **cluster for the green system**

### 2. Build and deploy image pipeline

**Pipeline**

You can see this  pipeline in the image called **Pipelines diagram.png** in the "Pipeline 2". You can see the **Jenkinsfile** in the folder **build-image-pipeline**.

**Result**

In there you use the **tidy** to **lint the HTML** and then we use **docker cli** to build the image and push it.

In there you use the **kubectl** to deploy the image to the cluster in the blue system and the add a alias record so that the domain 
udacitypinzoncloudcapstone.de redirect to the blue cluster. Then, with **kubectl** we deploy the image to the cluster in the green system and the add a alias record so that the domain 
udacitypinzoncloudcapstone.de redirect to the green cluster

**The blue and green deployment depends if you push to the green branch or to the blue branch**


