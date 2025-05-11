# DDOS Attack
* Distributed Denial-of-service on our infrastructure
  
  eg: suppose there is a hacker and they want to do DDOS attack against our application server.
  
  In this case they are going to launch multiple master servers and these servers are going to launch bots.
  
  All these bots are going to send a request to our application server. now our application is server is unable to handle this many requests
  
  and it will be denied service. Therefore, any normal user trying to connect to our application server will see that it is not accessible and not responsive

* In AWS, we can protect DDOS Attack by:
  > **AWS Shield standard**: protects against DDOS attack for ur website & applications,it is activated for all customers at no additional costs.
  
  > **AWS shield Advanced**: 24/7 premiun DDOS protection . it is costly($3000 per month for organisation)
  
  > **AWS WAF**: web application firewall , filter specific requests based on rules like ip addresses,HTTP headers,HTTP body etc
  
  > **cloudfront & Route 53**: gives protection by using global edge network

  > when combined with aws shield, provides attack mitigation at the edge locations.

# AWS Network Firewall (protects VPC entirely)

* This service protect ur entire Amazon VPC from Layer 3 to Layer 7 in any direction

# AWS Firewall Manager

*this service manages security rules in all accounts of your AWS organisation

*It supports VPC security groups across multiple accounts in an organisation

# Penetration testing on AWS

> this means testing ur own infrastructure to test your security

# Encryptions
2 types

1.**Data at rest**: data stored or archived on a device
  > on a hard disk, on a RDS instance, in s3 glacier deep archive etc

2. **Data in transit(in motion)**: data being moved from one location to another
   > Transfer from on-premises to AWS, EC2 to Dynamodb, etc.

# AWS KMS (key management service)

* AWS manages the encrption keys for us. and we can just define who can access this keys.

  > Encryption opt-in:
    for **EBS volumes**: we can choose to encrypt them with KMS
  > for **S3 buckets**: server side encryption of objects(SSE-S3 enabled by default,SSE-KMS opt in)

  >Encrption automatically enabled for:
    cloudtrail logs, s3 glacier & storage Gateway

* Types of KMS keys
  
  1.**Customer managed key:**
    > create,manage and used by the customer, can enable or disable
    
    > possibility of rotation policy (new key generated every year, old key preserved)
    
    > possibilty to bring your own key

  2. **AWS Managed key:**
     > created,managed and used on the customer's behalf by AWS
     
     > Used by AWS services(aws/s3, aws/ebs,aws/redshift)

  3.**AWS owned key:**
    > collection of keys that a service owns & manages to use in multiple accounts.

    > AWS can use thos eto protect resources in your account (but u can't view the keys)
    
# CloudHSM keys(Hardware security module)

* AWS provisions encryption hardware and cryptographic operations are performed

  ## AWS Certificate manager (ACM)

  * It is a service which provides easily provision, manage and delpoy SSL/TLS certificates.
 
  * These certificates are used to provide in-flight encryption for websites by providing an HTTPS endpoints.
 
  * ACM supports both public & private TLS certificates and it is free of charge for public TLS cert
 
  * Automatic TLS certificate renewal
 
  * Integratins with load TLS certs on
    
    . Elastic load balncers
    
    . cloudfront distributions
    
    . APIs on API gateway
    
 
  * **eg:**

   we have application load balancer and it is connected in the backend through HTTP to an autoscaling group with our EC2 instances. But we want endusers to have HTTPS exposed on our application. To do so we're using ACM, once ACM is connected to our domain & it allows us to provision & maintain TLS  certs. Then they will be loaded onto our application loadbalancer then ,loadbalancer automatically offers an HTTPS as an endpoint for our clients which allows us to inflight encryption over the public web

  ## AWS Secret manager

  * this service used for storing secrets
 
  * it has a capability for **rotation of secrets**
 
  * Automate generation of secrets on rotation (uses Lambda)
 
  *  **Integration with Amazon RDS**(MYSQL, Postgresql, Aurora)
 
  *  Secrets are encrypted using KMS

## AWS Artifact( not really a service)

* It is  a portal that provides customers with on-demand access to AWS complaince documentation & AWS agreements

* used to support internal audit or complaince

## GuardDuty

*  Amazon guardduty helps u do **intelligent threat discovery** to protect your AWS account

*  Guardduty uses machine learning algorithms, performs anamoly detection & uses 3rd party data to find threats

*  no need to install software, to enable it's just a one click ( 30 days trail)

*  Input data includes:

   > cloud trail event logs : unusual api calls, unauthorized deployments
     > cloudtrail management events : create vpc subnet, create trail,..
      > cloudtrail s3 data events - get object, list objects, delete objects,...
   
   > VPC flow logs - unusual internal traffic , unusual ip address
   
   > DNS LOGS
   

  * Can setup eventbridge rules to be notified in case of findings

  * Eventbridge rules can target AWS lambda or sns

  * can protect against cryptocurrency attacks 

## Amazon inspector

* This service only for EC2 instances, container images & lambda functions

* when needed, continuous scanning of the infrastructure is started

* package vulnerabilities (EC2, ECR & Lambda)

* network reachability(EC2)

* A risk score is associated with all vulnerabilities for prioritization


## Amazon Macie

* This service is  a fully managed data security and data privacy service that **uses machine learning and pattern matching to discover and protect your sensitive data in AWS**

* Macie specifically, identify and alert you to sensitive data, such as personally identifiable information (PII)

* PII will be in s3 buckets which is analyzed by macie to discover sensitive data and will  notify through eventbridge and they can have integrations into an SNS topic

  ## AWS Security Hub

  * It's a central security tool to manage security across several AWS accounts and automate security checks
 
  * Integrated dashboards showing current security and complaince status to quickly take actions
 
  * Automatically aggresgates alerts using AWS services & partner tools
 
  * we must enable AWS config
 
  ### Actions that can be performed only by the root user are:
  > change account settings(account name, email address, root user pwd, root user access keys)
  
  > view certain tax invoices

  > close  ur aws account
  
  > restore IAM  user permissions
  
  > change or cancel ur AWS support plan
  
  > Register as a seller in the reserved instance marketplace
  
  > configure an amazon s3 bucket to enable MFA
  
  > edit or delete an s3 bucket policy that includes an invalid vpc id or vpc endpoint    > signup for govcloud
  

  ## IAM access analyzer

  * it find outs resources shared externsally are :
    > s3 buckets, IAM roles, kms key, lambda functions, sqs queues, secret manager

* define **zone of trust** = AWS account or aws organisation
 
