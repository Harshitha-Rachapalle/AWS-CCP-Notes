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
    > 
# CloudHSM keys(Hardware security module)

* AWS provisions encryption hardware and crptographic operations are performed
   


  
