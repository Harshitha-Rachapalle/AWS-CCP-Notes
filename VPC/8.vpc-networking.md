# IP Address in AWS
* **IPV4**- Internet protocol version 4
  > **public IPV4** - can be used on the internet
   > When u create a EC2 instances, a new public ipv4 address is generated . when we stop it, ipaddress also disables

   > **Private IPV4** - can be used on private Networks (LAN) (eg: 192.879.0.9) such as internal AWS VPC
   > private IPV4 is fixed for EC2 instances even if you start/stop them

* **Elastic IP** -allows u to attach **a fixed public IPV4 address to EC2 instance**
  > note: All public IPV4 on AWS will be charged $0.005 per hour(including elastic IP)

* **IPV6** - Internet protocol version 6
  > Every IP address is public in AWS ( no private range)
  > eg: 2009:8998:577:fffff:gffg:ffgg:eeeee
  > IPV6 is free in AWS

# VPC & Subnets Primer
* **VPC** - Virtual private cloud . It's a private network to deploy your resources
  > A VPC is linked to a specific region
  > **Subnets**: within VPC  we have subnets which allows to partition of ur network and it is going to be associated with an availability zone
  > **Public subnet**: is a subnet that is accessible from the internet
  > **Private subnet**: is a subnet that is not accessible from internet
  > **Route tables**: to define access to the internet and between subnets
  > **Internet Gateways**: helps our VPC instances connect with the internet
  >  public subnets have a route to the internet gateway to be able to access the internet
  >  suppose, if u have an instance in a private subnet it is not going to be accessible from internet . if you want to give access to internet for downloading files , etc  for this we use a **NAT gateway**
  >  **NAT gateways(AWS- managed)** & **NAT Instances(self-managed)** allow ur instances in **private subnets** to access the internet while remaining private
  > we create a NAT gateway in our public subnet and we create a route from private subnet to NAT gateway and from NAT gateway to internet gateway and this will allow our private subnets to communicate through internet

# Network ACL & Security groups
* **NACL** network ACL is a firewall which controls **traffic from and to subnet**
  > NACL is at **subnet level** & can have "ALLOW" & "DENY" rules
  > Rules only include IP addresses
  > **Stateless**: return traffic must be allowed explicitly by rules

* **Security Groups**
  > A firewall which controls **traffic from and to an EC2 instance**
  > Security groups is at **EC2 Instance level** & can only have "ALLOW" rules
  > rules include ip addresses & other security groups
  > **stateful**: return traffic is automatically allowed, without any rules
  
# VPC Flow logs
* vpc flow logs are a log of all IP traffic going into ur interfaces.we can get
  > vPC flow logs
  > subnet flow log
  > Elastic network interface flow log

* By enabling flow log, we can monitor & troubleshoot connectivity issues. example:
  > subnets to internet
  > internet to subnets
  > subnets to subnets

* VPC flow log data can go to S3, cloudwatch logs, and Amazon data fiehose

# VPC Peering
* vpc peering is to connect two vpc privately using AWS network
* make them behave as if they were in the same network
* IP address range should not overlap then only we can do vpc peering
* Vpc peering connection is **not transitive** (i.e must be established for each VPC that need to communicate with one another)

# VPC Endpoints
* VPC end points gives a better security and low latency to access AWS services
* **Endpoints** allows u to connect to AWS services using a **private network** instead of public internet network

> **VPC endpoint gateway** is for Amazon s3 & DynamoDB
> **VPC Endpoint interface**: is for most services(including S3 & dynamodb)

**AWS private link**: it requires a (NLB) network load balancer(service vpc) and ENI(elastic network interface) consumer vpc

**Site to site VPN**:  
> This is to connect an on-premises vpn to aws vpc through public internet . The connection is automatically encrypted. we can connect this very quickly and there r some security issues bcz we r using public internet

**Direct connection(DX)**:
> Establish a physical connection between on-premises & VPC
> The connection is private, secure & fast
> cost is huge and takes atleast a month to establish connection

> on-premises : must use a customer gateway **(CGW)**
> AWS: must use a virtual private gateway **(VGW)**
> CGW & VGW are required for site to site vpn

# Transit Gateway
> for having transitive **peering between 1000's of VPC** and on-premises , hub & spoke (star) connection

> AWS transit gateway provides this functionality
> It works with Direct connect gateway, VPN connections
  
