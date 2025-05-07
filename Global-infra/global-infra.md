## Global application
* Global application is an application deployed in multiple geographies i.e in AWS they are regions or edge locations
* If we deploy into multiple regions then it will be **low latency** for users i.e user can access application very quickly from near by there regions
* **Disaster Recovery**
  > if an AWS region goes down (earthquake,storms,powershutdowns etc), still we can access the application in another region
* **Attack protection**
  >if hacker tries to attack the application , eventhough we can access applications in different regions bcz he can't attack at a time in all regions so we can be aware and conscious further to protect

# Route 53
* It is a managed Domain Name System(DNS)
  
* **DNS** is just like a phonebook where it stores rules & records.
  
* DNS helps clients understand how to reach a server through URLs
  
* In AWS, the most common records are:
  > www.google.com >> 12.34.56.56 == A record(IPV4)  [IF We r mapping this **url to IPV4** then it is **A record** )
  
  > if we r mapping this **url to IPV6** then it is called **Quadruple A record**
  
  > if we r mapping **hostname to hostname** it's called **CNAME**

   eg: search.google.com >> www.google.com == CNAME
  > if we r mapping a **host name into an AWS resource** it's called **Alias**

  eg: example.com >> AWS resource == Alias (ex: ELB, CloudFront, S3, RDS etc..)

## Routing policies
1. **Simple routing policy**
   > No health checks

   > our web browser will go into our DNS system(Route 53) and does a DNS query and gets an IPV4 as a result

 2. **Weighted Routing Policy**
    > This policy allows us to distribute the traffic across multiple ec2 instances
    
    > we use health checks

3. **Latency Routing policy**
   > suppose if we have deployed application globally then user will talk to the closest server whereroute 53 minimises to low latency

4. **Failover Routing Policy**
   >in this policy, we have a client and primary, Failover ec2 instances.
   
   >our DNS system will do a health check on primary if in case it fails then it'll redirected to the failovers this helps **disaster recovery**


# AWS CloudFront

* cloudfront is a content delivery network **(CDN)**

* It improves the read performance by caching the content of websites at different edge locations

* the content has been cached all over the world now the users have a low latency and this will improve the user experience

* AWS WAF web access control lists (web ACLs) to help minimize the effects of a distributed denial of service (DDoS) attack. For additional protection against DDoS attacks, AWS also provides AWS Shield Standard and AWS Shield Advanced.

## cloudfront - origins
1. **S3 bucket**
   > s3 bucket is used for distributing files and caching them at edge
   
   > for uploading files to s3 through cloudfront
   
   > clodfront & s3 buckets are secured using Origin Access Control(OAC)

2. **VPC origin**
   > If application hosted in private subnet then ALB, network load balancer, EC2  instances we can connect cloudfront directly to them privately.

3. **Custom Origin (HTTP)**
   >It could be a website hosted on Amazon s3 and we make sure that this website is enabled as a static s3 website
   
   >any public HTTP website

### cloud front vs s3 cross region replication

**Cloudfront**

> Global edge network

> files are cached

> Great for **static content** that must be available everywhere

**S3 cross region replication**

> must be set up for each region you want replication to happen

> Files are updated in near real-time

> Read only

> Great for dynamic content that needs to be available at low latency in few regions

## S3 Transfer Aceleration

> AS we know S3 buckets are linked to only one regionand sometimes u r looking to transfer files from all around the world into one specific S3 buckets.

> S3 transfer acceleration increases transfer speed by transferring file to an AWS edge location which will forward the data to s3 bucket in target region


## AWS Wavelength
ultra low latency

wavelength zones are infrastructure deployments embedded within the telecommunication providers datacenters **at the edge of the 5G networks**.

## Global Applications Architecture

1. **Single region, single AZ**
2. **single region, multi AZ**
3. **Multi region, active-passive**
4. **Multi region, active-active**

### AWS Outposts
Deploy outposts racks in ur own datacenters to extend AWS resources

this service can be used to run AWS infrastructure and services on-premises for a hybrid cloud architecture
