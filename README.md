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

### Important

eksctl uses cloudformation to deploy the cluster!!!!!!!

### 1. Create clusters pipeline

**Pipeline**

You can see this  pipeline in the image called **Pipelines plan.png** in the "Pipeline 1". You can see the **Jenkinsfile** in the folder **create-clusters-pipelines**.

**Result**

In there you use the **eksctl** to create the **cluster**. Please look at the image: cluster.png

### 2. Deploy containers pipeline

**Pipeline**

You can see this  pipeline in the image called **Pipelines plan.png** in the "Pipeline 2". You can see the **Jenkinsfile** in the folder **deploy-containers-pipeline**.

**Result**
Then, in there you use the **tidy** to **lint the HTML**. Please look at the image: lint.png

Then, we use **docker cli** to build the image and push it. Please look at the images: build-image.png push-image.png docker-image-repository.png


In there you use the **kubectl** to deploy the image to the cluster in the blue and green pod and create a **service** that redirects traffic to the blue pod. Please look at the images: deploy-blue-container.png deploy-green-container.png service-redirect-blue.png

Then, the **service** is updated to redirect traffic to the green pod. Please look at the image: service-redirect-green.png

Then, the website can be access using the URL of the service and the port. Please look at the images: website.png service-pods.png

