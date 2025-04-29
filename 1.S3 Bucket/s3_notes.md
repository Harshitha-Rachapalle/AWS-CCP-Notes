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
