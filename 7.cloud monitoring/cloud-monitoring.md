# Amazon cloudwatch metrics
> cloud watch provides metrics for every services in AWS

> Metric is a variable to monitor (CPU Utilization, Networking...)
> Metrics have timestamps
> we can create cloud watch dashboards for metrics

### Important Metrics
**EC2 instances**: CPU utilization, status checks, Networks(not RAM)
RAM is not available for ec2 metrics

* These metrics u get every 5 minutes by default
* we can enable detailed monitoring which is more expensive to get these metrics for every 1 min

**EBS volumes**: where u store data and u get information of disk read & writes that r happening

**S3 buckets**: bucket size ,bytes, no.of objects, all requests

**billing**: total estimated charge (only in us-east-1)

**custom metrics**: if we don't find any metrics we can push/create a custom metric

## cloudwatch Alarms

* Alarms are used to trigger notifications for any metric

* Alarm actions cam be...
  **Autoscaling**: increase or decreas eEC2 instances "desired "
 count

**EC2 Actions**: stop, start, terminate,reboot or recover an EC2 instance
  
  **SNS notifications**: send a notification into an SNS topic
  * we can mention time at what time alarm should trigger

  * eg: creating a billing alarm on the cloudwatch billing metric

## cloudwatch logs

* it is used to collect log files. with this files user can troublesoot the problem.

* we can collect logs from:
  **Elastic beanstalk**: collection of logs from application
  **ECS**: collection from containers
  **AWS Lambda**: collection from function logs
  cloud trail based on filter
  **cloudwatch log agents**: on ec2 machines or on-prremises servers
  **Route 53**: log DNS queries

  ### cloudwatch logs for EC2
  * By default, no logs from your EC2 instance will go to cloudwatch
  * u need to run a cloudwatch agent on EC2 to push the log files u want for this we should have IAM permissions
  * cloudwatch logs are hybrid , this works on EC2 & on-premises too
  
### cloud watch Events (Eventbridge)
* Schedule cron jobs
* eg: lamda function for evrery 1 hr
* eg: whenever we need to give alerts for security team, when someone is going to login using the root user, the rule is that we shouldn't use root user
* so,now team need to react to IAM root user sign in events  and send SNS topic with email notification

### AWS Cloudtrail

* provides audit for ur aws account and it is enabled by default
* cloudtrail will get an history of all **API calls within ur aws account**
  eg: if some one uses console, SDK, CLI, AWS services all this history will be stored
* can put logs from cloud trail into cloudwatch logs or s3
* if a resource is deleted in AWS, investigate cloudtrail first

* **cloudtrail insights** : automated analysis of ur cloudtrail events
* **x-ray**: trace requests made through ur distributed applications
* **AWS Health dashboard**: status of all AWS services across all regions
* **AWS account health dashboard**: aws events that impact ur infrastructure
  

  
  
