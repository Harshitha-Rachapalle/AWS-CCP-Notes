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
  
     
   
