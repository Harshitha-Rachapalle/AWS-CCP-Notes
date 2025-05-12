* In cloud, when u want to have a good architecture u need to stop guessing your capacity needs

  instead u should use autoscaling, and scale based on actual demanding of ur system

* you should test ur system at production scale

* cloudformation(IAC) is important for automate to make architectural experimentation easier

## AWS Cloud best practices -Design principles

* Scalability: vertical & horizontal

* Disposable resources: servers should be disposable & easily configured

* Automation: serverless, IaC, Autoscaling..

* Loose Coupling: monolith applications should break into smaller, loosely coupled components.

* Sevices, not servers: Don't use just EC2 , instead use managed services, databasrs, serverless etc

## 6 pillars of architecting system

### 1. operational excellence

* It has ability to run & monitor systems to deliver business value and continuos improve supporting processes & procedures

* Design principles:
  > perform operations as code - infrastructure as code

  > Make frequent, small, reversible changes
  
  > Refine operations procedures frequently
  
  > Anticipate failure
  
  > learn from all operational failures
  
  > use managed services

### 2. security

* It has ability to protect information, systems, and assets while delivering business value through risk assesments and mitigation strategies

*  IAM, Detective controls like AWS config, AWS cloud trail, cloudwatch.

*  Infrastructure protection : Amazon cloudfront, Amazon VPC, AWS shield, WAF, Inspector

*  Data protection : kms, s3, elb, ebs, rds

### 3. Relaibility

* Ability of a system to recover from infrastructure or service disruptions, dynamically acquire computing resources to meet demand, and mitigate disruptions such as misconfigurations


### 4. Performance efficiency

* Ability to use computing resources efficiently to meet system requirements, and to maintain thar efficiency as demand changes & technology evolve

### 5. cost optimization

* Ability to run systems to deliver buisness value at the lowest price point

  ### 6. sustainability

  * It has ability to minimise the environmental impacts of running cloud workloads
