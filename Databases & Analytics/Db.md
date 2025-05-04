* If u want to store data in structured way , we use database
* you define relationships between your datasets

  ## Relational Database Service (RDS)
  * Looks just like excel spreadsheets, with links between them.
    
  * we use **SQL language** to perform queries/lookups
 
  * It allows u to create databases in the cloud that are managed by AWS
    
    >These databases might be postgres,mysql,mariadb,oracle,microsoft sql server,IBM DB2, Aurora(AWS proprietary database)

   * **advantaages**
    > RDS is a managed service:
    
     i.e provisioning is automated and  patching of OS will be done by AWS.
  
   continuous backups and restore to specific timestamp.

   monitoring dashboards

  Read replicas for improved read performance

  Multi AZ setup for disaster recovery

  Maintenance windows for upgrades

  scaling capability (vertical & horizontal)

  storage backend by EBS

  **we can't SSH into our instances**( we r using service which is entirely provided by AWS)
  
  
  ## NoSQL Databases
  * NoSQL = non-SQL = non relational databases
    
  * NoSQL databases are purpose built for specific data models and for building modern application
    
  * flexibility,scalability, high performance, high functional
    
    Eg: key-values,document, graph, search databases
    
    **NoSQL data example**:JSON document
    javascript object notation(json)
    DynamoDB, DocumentDB

    ## Amazon Aurora
    * not open sourced
    * it works same as RDS, we have our ec2 instances connecting directly into AWS Aurora
    * **postgresql and mysql are both** supported as **Aurora db**
    * Aurora is "AWS cloud optimized" and claims 5x performance improvement over MYSQL on RDS, over 3x performance of postgres on RDS
    * Aurora storage automatically grows in inceremnets of 10 gb , upto 128 TB
    * Aurora costs more than RDS(20 % more) - but its more efficient
    * Not in free tier

    ## Amazon Aurora serverless
    * **postgresql and mysql are both** supported as **Aurora serverless db**
    * There is no management bcz u don't manage servers
    * no capacity planning needed
    * pay per second, can be more cost effective than provisioning
    * **usecases**: good for infrequent, intermittent or unpredictable workloads
    * **how it works?**
      > from clients perspective, it connects to a proxy fleet(managed ny aurora), then aurora is
       going to instantiate database instances when it needs to scale up or down and these aurora databases are going to
      be sharing same storage volumes


  ## RDS Deployments
  ### Read Replicas:
  * Scale the read workload of ur DB
  * can create upto 15 read replicas
  * Data is only written to the main DB
  eg: let's take the example of ur application that reads from ur main RDS database. it might have multiple read replicas

### Multi AZ
* In case of AZ outage or failover we can use other availability zone(high availaibility)
* Data is only read/written to the main database
### Multi region(Read replicas)
*Disaster recovery in case of region issue
*Local performance
*replication cost

## Amazon Elastic cache overview
* Elasticcache is to get managed redis or memcached
* caches are **in-memory databases** with high performance, low latency
* Helps **reduce load off databases for read intensive workloads**( the idea is that
  if we have a RDS database , we're doing a lot of query on it,instead of it we can use a cache reduce the pressure
  off of the database by making sure the queries are directly going onto my in-memory database throgh elasticcache)

  * **ElasticCache** is  a managed database where AWS takes care of OS maintenance, patching, optimizations,set up configurations, monitoring, failure recobery & backups.

## DyanamoDB
* Fully managed highly available with replication across 3 Availability zones(AZ)
* **NoSQL database** - not a relationship database
* scales to **massive workloads & distributed "serverless" database**
* **single digit millisecond latency**- **low latency**
* low latency, high performance
* INtegrated with IAM for security, authorization & administration
* Low cost & auto scaling capabilities
* Standard & infrequent accees(IA)
  ### dynamodb-type of data
  * It's a key/value database
 ### Dynamodb accelerator -DAX(i.e used as cache)
 * Fully managed in-memory cache for dynamodb
 * 10x performance improvement i.e when accessing dynamodb tables it has **microseconds latency**
 * **DAX** is only used for and is integrated with DynamoDB, while ElasticCache can be used for other databases
 ### Dynamodb - Global Tables
 * dynamodb table accessible with **low latency in multiple-regions**
 * eg: suppose we have dynamodb table in us-east-1 and we'll setup as a global table
   where users can read/write the dynamodb table.But for us it is possible to set up a **2-way replication** for this
   global table so we can create a global table in paris(eu-west-3). now wkt both the regions have a same data.
   users, who r close to paris region  can access global table with low latency.
* read/write access to any region of AWS on this global table, makes it an **Active-Active replication**


## Redshift Overview (analytics & data warehousing)
* Redshift is based on postgresql , but it's not used for OLTP(Online transaction processing)
* It is used for **(OLAP)- online analytics processing**
* Load data once evey hour, not in every second
* Data is stored as cloumns (i.e **column storage**)
* **pay as you go** based on the instances provided
* has a SQL interface for performing Queries
* It also integrated with BI tools such as AWS Quicksight or tableau to create dashboards for differnt warehouses
* It has- redshift serverless

## Amazon EMR(elastic map reduce)
* EMR helps creating **Hadoop clusters(Big Data)** to analyze and process vast amount of data
* we can create a cluster that made up of hundred's of ec2 instances that will be collaborating together to analyze your data
*  EMR takes care of provisioning of EC2 instances and configuring them so that they can work & analyse together data from a big data perspective.
*   Autosscaling and integrated with spot instances
*   **Use cases:** data processing, machine learning , web indexing, big data etc

## Amazon Athena( serverless SQL query to analyse S3 objects)

## Amazon Quick sight
* Serverless machine learning-poered buisness intelligence service **to create interactive dashboards**
* Integrated with RDS, Aurora, Athena, Redshift, S3 etc
* **Use cases:** buisness analytics, building visualizations, perforn ad-hoc analysis,get buisness insights using data

## DocumentDB
* it's **no sql database**
* documentDB is same for **mongoDB**
* MongoDB is used to store, query, and index json data
* Similar "deployment concepts" as Aurora i.e read replicas, multi AZ, multi region
* fully managed, highly available with replication across 3AZ
  
## Amazon Neptune
* It is fully managed **graph database**
* A popular **graph dataset** would be a **social network**
* highly available  across 3AZ, with upto 15 read replicas
* build & run applications working with highly connected datasets
* can store ypto billions of relations & query the graph with milliseconds latency
* Great for knowledge geaphs(wikipedia),fraud detection, recommendation engines, social networking

## Amazon TimeStream
* fully managed, fast, scalable, **serverless timeseries database**
* Automatically scales up/down to adjust capacity
* **built in time series analytics** functions

## Amazon QLDB (Quantum ledger database)
*ledger is a **book recording financial transactions**
*fully managed serverless 

## Amazon managed blockchain
* It is a decentralized blockchain
* compatible with the frameworks **Hyperledger fabric** and **Ethereum**

## Amazon Glue
* Managed **extract, transform & load** (ETL) service
* useful to prepare & transform data for analytics
* fully serverless service

## Database migration service (DMS)
* we use **Source DB** and once we extract the data we'll run an ec2 instance that will be running the DMS software & we'll extract data from source database
  and then DMS will insert the data back into target DB.
* With DMS we get a quick and secure database migration
* The souce db remains available during migration
* supports:
  homogeneous migrations eg: oracle to oracle
  heterogeneous migrations eg: microsoft sql server to aurora




  
  
