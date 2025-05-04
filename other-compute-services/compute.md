# Docker
* Docker is a software development platform to deploy apps
* Apps are packaged in **containers** that can be run on any OS
* scale containers up & down very quickly in seconds
* **Docker Images** are stored in docker respositories
  > public : **dockerhub**
  > private : **ECR**(Elastic container registry)
* Docker is a sort of virtualization technology, but not exactly
* containers are light weight which doesn't have complete OS
* Once docker daemon is running we can run many containers


# ECS (Elastic container service)
* used to launch docker containers on AWS
* we must create infrastructure such as ec2 instances and provision them
* AWS takes care of starting / stopping containers
* has integrations with Application load balancer(ALB)

# Fargate (serverless)
* it is a serverless offering provided by AWS
* You donot need to provision the infrastructure(ec2 configuration)
* AWS just runs containers for you based on the cpu/RAM u need

# ECR
* Private Docher registry on AWS
* Where u store docker images so they be run by ECS or fargate

# Amazon EKS
* Allows u to **launch managed kubernetes clusters** on AWS
* Kubernetes is  an open source system for management, deployment, and scaling of containerized apps
* containers can be hosted on:
  >EC2 instances
  >Fargate(serverless)

# Lambda
* suppose, if we use ec2 server, we have virtual servers in the cloud and we r bounded with
  some memory i.e by RAM & CPU. It is continuously running eventhough we don't use some times
  and if we want to scale , we use autoscaling groups to add/ remove servers. which may result in slow and complicated.

*  **Lambda -no servers** where we just have virtual functions
*  these functions r limited by time, i.e they are intended for short type of executions
*  **run on-demand**
*  **pricing**: pay per request and compute time
*  **Event-driven**: functions get invoked by AWS when needed
*  integrated with many programming languages
*  Easy monitoring through AWS cloud watch
*  limited temporary disk space
*  limited runtimes

# Amazon API gateway
* building a **serverless API** & scalable
* supports RESTful APIs and websocket APIs
* support for security, user authentication, API keys, monitoring
* fully managed service for developers to easily create, publish, maintain, monitor & secure APIs

# AWS Batch
* Batch is a fully managed batch processing service at any scale
* **batch job** is a job that has a start and an end
* Batch will dynamically launch EC2 instances or spot instances to accomodate with
  with load that u have to run these batch jobs.
* Batch provisions with the right amount of compute/memory
* you submit or schedule batch jobs and AWS batch does the rest
* Batch jobs are defined as **Docker images and run on ECS**
* Helpful for **cost optimization** and focusing less on the infrastructure
* relies on ec2(managed by aws)
* rely on ebs/instance store for disk space

# Amazon lightsail
* virtual servers, storage, databases and networking
* **low & predictable pricing**
* simpler and aliernative to using EC2,RDS,ELB,EBS,Route 53 etc..
* great for people with little cloud experience
* we can setup notifications & monitoring of ur lightsail resources
* has high availabilty, but no auto scaling
