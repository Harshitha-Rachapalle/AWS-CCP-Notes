# cloud formation

* it is a template where we can create infrastructure, for any resource
* for exampl, within cloud formation template, you say
  > I want a security group
  
  > I want 2 EC2 instances using these security group
  
  > I want an S3 bucket
  
  > I want a load balancer(ELB) in front of these machines
  
 * Then cloud formation creates those for you, in the right order with the exact configuration that u specify

   ## Benefits

   1. **Infrastructure as code**
      > no resources are created manually
      
      > changes to the infrastructure are reviewed through code review

   2. **cost**
      > you can estimate the cost of your resources using the cloudformation template
      
      > savings strategy: in dev, u could automation deletion of templates at 5pm and recreated at 8 am safely

   3. **productivity**
      > ability to destroy & recreate an infra on the cloud on the fly
      
      > automated generation of diagram for ur template
      
      > declarative programming
      
      >  Leverage existing templates on the web
      
      > leverage the documentation

   4. **Supports all AWS resources**
      > we can use "custom resources" for resources that r not supported.

  # CDK( cloud development kit)
  * we can define cloud infrastructrure using a familiar language:
    > javascript/typescript. puthon, java and .Net
  * The code is "compiled" into a cloud formation template(yaml/json)
  * therefore u can deploy infrastructure and application runtime code together
    > Great for lambda functions
    
    > great for docker containers in ECS/ EKS

# Beanstalk

when we have deployed a web application in AWS, we typically follow a architecture called 3-tier architecture.

so users talk to a load balancer that could be in multi AZ's. then load balancer will forward traffic to EC2 instances managed by autoscaling groups and these EC2 instances need to store data somewhere that might be database such as RDS(relational database service) read/write data. If they need for an in-memory cache, then they can also use elastic cache to store or  retrieve data . we can reproduce this efficiently through **Beanstalk**

## AWS Elastic Beanstalk Overview
> It is a developer centric view of deploying an application on AWS

> It uses all components like EC2, ASG,ELB,RDS etc

> Beanstalk is a platform as a service **(paas)**

> It's a managed service where instance configuration/ OS is handled by Beanstalk

> Loadbalancing & Autoscaling

> Application health monitoring & responsiveness

> Application code is the responsibility of the developer and supports for many platforms i.e programming language

 * Three architecture models in beanstalk are
   >**single instance deployment** : good for dev
   
   > **LB +ASG**: great for production or preproduction web applications
   
   > **ASG only**: great for non web-apps in production (workers,etc..)

### Beanstalk-Health monitoring
> health agent pushes metrics to **cloudwatch**

> checks fo app health, publishes health events

### AWS code deploy overview

* we can deploy our application automatically
  
* works with EC2 instances & on-premises servers i.e upgrading fron V1 TO V2

* **Hybrid** service

* servers/instances must be provisioned and configured ahead of time with codedeploy agent

### AWS Codebuild

* building a code i,e compiles source code, run tests amd produces packages that are ready to be deployed
* code buils is a fully managed and serverless

* continuously scalable and highly available and secure

* pay-as-you-go prcing - only pay for the build time


### AWS code pipeline
> code >> build >> test >> provision >> deploy

> it's like CI/CD





  
     
   
