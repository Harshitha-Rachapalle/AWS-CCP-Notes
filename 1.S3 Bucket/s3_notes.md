# Amazon s3 usecases
> Backup & storage (eg:it could be files,disc storage etc)

> Disaster recovery  (eg:if u'll move ur data to another region, incase ur region is down then ur data is backed up somewhere else)

> Archive (we can archive files and then we can retrieve for cheaper price only)

> Hybrid cloud storage (suppose u have storage on **on premises** and u won't expand on cloud then we can use s3 )

> Application hosting

> media hosting (vedios,images)

> Data lakes & big data analytics

> software delivery

> hostic static websites

### Note  (s3 - buckets)
> S3 allows people to store objects (files) in " buckets"(directories)

> Buckets must have a globally unique name (across all regions all accounts)

> Buckets are defined at **region level** , s3 looks likes a global service but buckets are created in a region

### s3 - objects
> objects(files) have a key

> **key** is the FULL path i.e  s3://my-bucket/my_file.txt

> key is composed of prefix + object name   >> s3://my-bucket/my_folder/another_folder/my_file.txt

> object values are the content of the body

> max object size is 5TB(5000GB)  .  If uploading more than 5TB, must use "multi part upload"

# Amazon s3 - security
* user based
  >IAM policies- which api calls should be allowed for a **specific user** from IAM
* Resource based
  > Bucket policies - bucket wide rules from the s3 console-allows cross account
  > Object Accees control list(ACL) - finer grain(can be disabled)
  
  > Bucket  Accees control list(ACL) - less common(can be disabled)
* Encryption
  >encrypt s3 objects using encryption keys
* If you get **403 forbidden error** make sure bucket policy allows public reads
  
# s3 bucket -versioning
* we can version our files at **bucket level**
  
* it's a best practice to version buckets which restores a version if it is unintended delete

# s3 replication
there r 2 types 

1.CRR(cross region replication)

2.SRR(same region replication)

eg: suppose we have s3 bucket in (eu-west-1) and other s3 bucket in (us-east-2) region to do an asyncronous replication >>> we must enable versioning in source and destination buckets 

>must give proprer IAM permissions to s3

# s3 storage classes
>**Amazon s3 standard-general purpose** (s3 standard )
  **.** 99.99% availabilty
  **.** used for frequently accessed data
  **.** low latency(fast response) and high throughput(doing more work/requests in few second)
  **.** sustain 2 concurrent facility failures
 **use cases**: Big data analytics,mobile and gaming applications,content distribution  etc

> **Amazon s3 standard- infrequent access(IA)** (s3 standard-IA)
 **.** for data less frequently accessed,but requires rapid access when needed
 **.** Lower cost than s3 standard (but u'll have a cost on retrieval)
 **.** 99.9% availabilty
 **use cases**: Disaster recovery, backups 

> **Amazon s3 one zone -infrequent access** (s3 one zone-IA)
  **.** High durability(99.999999999%) 11 9's in a single AZ
  **.** data lost when AZ is destroyed
  **.** 99.5 % availability
  **use cases**: Storing secondary backup copies of on-premise data, or data you can recreate.

**s3 glacier storage classes** are low cost object storage for archiving/backup 
**pricing**: price for storage + object retrieval cost

> **Amazon s3 Glacier instant retrieval**
 for retrieval , it takes milliseconds. it's great  for data accessed once a quarter  .min storage duration : 90 days

> **Amazon s3 Glacier flexible retrieval**
for retrieval data back, expedited(1 to 5 min), standard(3 to 5 hrs), bulk(5 to 12 hrs)   min storage duration : 90 days

> **Amazon s3 Glacier deep archive**(for long term storage)
for retrieval data back, standard(12 hrs), bulk(48 hrs) time
min storage duration : 180 days

>**Amazon s3 intelligent tiering**
small monthly monitoring & auto tiering fee . there r no retrieval charges

>> we can move between classes manually or using s3 lifecycle configurations
>> s3 have **high availabilty** and **high durability(11 9's)**

## s3 encryption
* **server side encrption(default)** server encrpts the file afer receiving into bucket
* **client side encyption** encrypts the file before uploading it

 



