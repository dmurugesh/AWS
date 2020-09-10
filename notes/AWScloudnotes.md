  # AWS Cloud practitioner exam # 

 ## Table of contents ##
 1. What is Cloud Computing 
 2. IAM - Identity and Access Management
 3. EC2 - Cloud Compute


 ## What is Cloud Computing ##
 
 * What is server composed of - 
    * CPU(Compute)  
    * RAM(Memory)
    * Storage(data) 
    * Database(Store data in a structured way) 
    * Network(Routers,switch, DNS server)
 * IT Terminology
    * Network - Cables,routers and serers connected with each other 
    * Router - A networking device that forqards data packets b/w computer networks. They know where to send your packets on the internet
    * Switch - Takes a  packet and send it to the correct server/cilent on your network
 ```
 Work Flow 
 
 Cilent  --> Router --> Switch --> various cilents 
 ```
 * **Cloud** **Computing** is the on-demand delivery of computer power, database storage applications and other IT resources
 * Though a cloud services platform with pay-asyou-go pricing.
 * Simple way to access servers, storage databases and set of application services
 * Three types of cloud 
   1. Private cloud 
      * Cloud service used by a single organization, not exposed to public. 
      * Security for senstive applications, Meet specific bussiness needs
      * eg: rockspace
   2. Public cloud 
      * Cloud resources owned and operated by thrid party cloud service provider delivered over the internet 
      * eg: Google cloud, AWS, Microsoft Azure
   3. Hybrid cloud
      * Keep some servers on premises and extend some capabilities to the cloud 
      * Control over senstive assests in your private infrastructure
 * Five characteristics of cloud computing 
    1. On-demand self service             - use without human interaction from the service provider
    2. Broad network access 		  - can be accesed by diverse cilent platform
    3. Multi-tenacy and resouce pooling   - multiple customer can share the same infrastructure and applications with security and privacy
    4. Rapid elasticity and scalabilty    - quickly and easily saclebased on demad
    5. Measured service  		  - usage is measured pay only for your usage 

 #### Types of cloud Computing ####
  1. Infrastructure as a service (IaaS)
      * Provide building block for cloud IT
      * Provides networking, computers, data storage space
      * Highest level of flexibilty 
      * Easy parallel with traditional on-premises IT
      * eg : Amazon EC2 (on AWS), GCP,Azure, Rackspace, Digital Ocean, Lincode
  2. Platform as a Service (PaaS)
      * Removes the need for your organization to manage the underlying infrastructure 
      * Focus on the deployment and management of your application.
      * eg: Elastic Beanstalk (on AWS), Heroku, Google App engine(GCp), Windows Azure 
  3. Software as a Servie (SaaS)
      * Completed product that is run and managed by the service proider 
      * eg: Many AWS service (ex: Rekognition for machine learning), Google Apps (gmail), Dropbox, Zoom

 ## IAM (Identity and Access Management) ##

 * Root account created by default, should not be used or shared
 * Users are prople within organisation, and can be grouped
 * Groups only contain users, not groups
 * Users dont have to belong to a group and user can belong to multiple groups

 #### IAM: Permissions ####
 * Users or group can be assigned JSON documents called policies
   eg : for policies 

   ![Linux Directories](/notes/img/iampolicies.png?raw=true "Title")

 * Policies define the permission of the user.
 * In AWS you apply the least privvilege principle: dont give more permissions than a user needs
    eg: If user need 3 permisisions just give access to 3 permissions only 
 * Tags are way for you to mark the users and add some attributes
 * Check the video 2 gor how to create user and groups 

 #### IAM Policies ####

 * IAM policies are nothing but the giving permisssion access to each user/group
 * IAM password policies - one method of protecting the users and groups from being compromised.
 * IAM Passwor polices are 
    * Strong Password = Higher security for your account
    * Allow all IAM users to change their own passwords
    * Requires users to change their password after sometime (password expiration)
    * Prevent password-reuse 
 * Password policy is really helpful agnist brute force attacks on your account
 * MFA (Multi Factor Authentication) - Second method of protecting the users and groups from being compromised.
 * MFA is most recommened to use
 * MFA = **"password you know + security devvice you own"**
 * Benfits of MFA - IF a password is stolen or hacked the account is not compromised.
 * MFA device option is AWS
    * Google Authenticator - phone only
    * Authy - multi device 
    * Universal 2nf facotr (U2F) security key  - Yubikey an 3rd party 
    * Hardware Key Fob MFA Device - Germalto (3rd Party)
    * Hardware key Fob MFA device for AWS GovCloud(US) - SurePassID

 #### To generate AWS access keys & Install AWS CLI ####
 
 * Never use Root account to create security credentials. 
 * Access keys are generated therough AWS cnsole
 * Users manage their own access keys 
 * Access keys are secret, just like a password. Dont share them 
 * Access Key ID ~= Username
 * Secret Access Key ~= password
 * To create Access key us IAM user account 
     * Go to users 
     * click on the **user** and click on **"Security Credentials"** 
     * Click on **"Create Access key"** and download and saw .csv file 
 * To install AWS CLI  
    * Go to link: https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-windows.html
    * Download the AWS CLI MSI installer for Windows (64-bit)
    * Install 
 * To Check if AWS CLI is intall on your command prompt type **"aws --version"** if installed it show like this => aws-cli/2.0.45 Python/3.7.7 Windows/10 exe/AMD64
 * Uninstall the AWS CLI version 2 from Windows
    * Open command prompt 
    * Type **"C:\> appwiz.cpl"**
 * To Configure AWS CLI 
   ```
    aws configure          - use to configure aws, add AWS access key ID & Secret access key & region 
    aws iam list-user      - Gives the list of all users associated with in the account
   ```
 * Aws management console and CLI provide similar kind of information

 #### IAM Roles for Service ####
 
 * Some AWS services that we'll be launching throughout will need to perform actions on our behalf, on our account and to do these actions,  they are just like user need kind of permissions, So we need assign permission to AWS services through IAM Role
 * IAM roles are a secure way to grant permissions to entities that you trust.
 * Common rules 
    * EC2 Instance Roles
    * Lambda Function Roles 
    * Rules for CloudFormation
 * To Create Roles
 ```
  1. Click on roles in LHS
  2. Then click on create role button 
  3. Select apporparaite use entity and use case and then click on next permissions
  4. Then select on poilices and click on next:Tags 
  5. Then add tag f you want and click on next:review
  6. Provide Role name and click on Create role 
 ```
 
 #### IAM Security Tools ####
 
 * We can create IAM Credentials Report (account-level) 
    * A report that lists all your account's user and the status of various credentials 
 * IAM Access Advisor (user-level) 
    * Access advisor shows the service permissions granted to a user and when those services were last accessed
    * You can use this information to revise your poliies

 ## EC2 - Elastic Compute Cloud ##

 ### Amazon EC2 ###
 
 * EC2 is one of the most popular of AWS’ offering 
 * EC2 = Elastic Compute Cloud = Infrastructure as a Service
 * It mainly consists in the capability of :
	* Renting virtual machines (EC2)
	* Storing data on virtual drives (EBS)
	* Distributing load across machines (ELB)
	* Scaling the services using an auto-scaling group (ASG)
 * Knowing EC2 is fundamental to understand how the Cloud works

 ### EC2 sizing & configuration options ###
 
 * OS - Linux or Windows
 * How much compute power & cores (CPU)
 * How much random-acess memory (RAM)
 * How much storage space 
     * Network attacched (EBS & EFS)
     * hardware (EC2 Instance Store)
 * Network card: speed of the card , Piblic IP address
 * Firewall rules : security group
 * Bootstrap script (configure at first launch): EC2 User data
 * EC2 Example 
   
     ![Linux Directories](/notes/img/ec2eg.png?raw=true "Title")

 ### Introduction to Security Groups ###

 * Security groups only cotain allow rules 
 * Security groups are the fudamental of network sercurity in AWS
 * They control how traffic os allowed into or out of our instances
 * Security groups rules can reference by IP or by security group 
 * Security groups are acting as "firewall" on EC2 instance 
 * regulate : 
    * Access to ports
    * Authorised IP ranges - IPv4 and IPv6
    * Control of inbound network (from other to the instance)
    * Control of outbound network (from the instance to other)
 * Class Ports to Know 
   * 22 = SSH (Secure Shell) - log into a Linux instance
   * 21 = FTP (File Transport Protocol) – upload files into a file share
   * 22 = SFTP (Secure File Transport Protocol) – upload files using SSH
   * 80 = HTTP – access unsecured websites
   * 443 = HTTPS – access secured websites
   * 3389 = RDP (Remote Desktop Protocol) – log into a Windows instance
 
 ### EC2 Instances Purchasing Options ###

 * On-Demand Instances:short workload, Predictable pricing
 * Reserved: (Minimum 1 year)
     * Reserved Instances: long workloads
     * Convertible Reserved Instance: long Workloads with flexible instances
     * Scheduled Reserved Instances: exacmple- every thursday b/w 3 and 6
 * Spot instances: short workloads,cheap, can lose instances (less reliable) 
 * Dedicated Hostts: book an entire physical server, control instance placement
 
 #### Ec2 On Demand ####
 
 * Pay for what you use:
     * Linux - billing per second, after the first minute
     * All other operating systems (ex: Windows) - billing per hour
 * Has the highest cost but no upfront payment
 * No long-term commitment
 * Recommended for short-term and un-interrupted workloads, where you can't predict how the application will behave
 
 #### EC2 Reserved Instances ####
 
 * Up to 72% discount compared to On-demand
 * Reservation period: 1 year = + discount | 3 years = +++ discount
 * Purchasing options: no upfront | partial upfront = + | All upfront = ++ discount
 * Reserve a specific instance type
 * Recommended for steady-state usage applications (think database)
 * Convertible Reserved Instance
    * can change the EC2 instance type
    * Up to 45% discount
 * Scheduled Reserved Instances
    * launch within time window you reserve
    * When you require a fraction of day / week / month
    * Commitment for 1 year only

 #### EC2 Spot Instances ####

 * Can get a discount of up to 90% compared to On-demand
 * Instances that you can “lose” at any point of time if your max price is less than the current spot price
 * The MOST cost-efficient instances in AWS
 * Useful for workloads that are resilient to failure
    * Batch jobs
    * Data analysis
    * Image processing
    * Any distributed workloads
    * Workloads with a flexible start and end time
 * Not suitable for critical jobs or database
 
 #### EC2 Dedicated Hosts #### 

 * An Amazon EC2 Dedicated Host is a physical server with EC2 instance capacity fully dedicated to your use. Dedicated Hosts can help you address compliance requirements and reduce costs by allowing you to use your existing server-bound software licenses.
 * Allocated for your account for a 3-year period reservation
 * More expensive
 * Useful for software that have complicated licensing model (BYOL – Bring Your Own License)
 * Or for companies that have strong regulatory or compliance need

 #### EC2 Dedicated Hosts #### 

 * Instances running on hardware that’s dedicated to you
 * May share hardware with other instances in same account
 * No control over instance placement (can move hardware after Stop / Start)
 * Pricing Example
  
   ![Linux Directories](/notes/img/pricingeg.png?raw=true "Title")
 
 #### Shared Responsibility Model for EC2 ####
 
 ![Linux Directories](/notes/img/sharedec2.png?raw=true "Title")


 ## EC2 Instance Storages ##
 
 ### EBS Overview ###
 
 * An EBS(Elastic Block store) Volume is a network drive you can attach to youur instances while they run
 * It allows your instances to persist data, even after their termination. ie ie even after the instance is terminated. We can recreate an instance, and mount the same EBS volume from before,and we will get back our data.
 * They can only be mounted to one instance at a time (at the CCp level)
 * They are bound to a specfic availability zone
 * Analogy: Think of them as a  "network USB stick"
 * Free tier: 30 GB of free EBS storage of type gp2 per month

 ### 1. EBS Volume ###
 
 * It’s a network drive (i.e. not a physical drive)
    * It uses the network to communicate the instance, which means there might be a bit of
      latency
    * It can be detached from an EC2 instance and attached to another one quickly
 * It’s locked to an Availability Zone (AZ)
     * An EBS Volume in us-east-1a cannot be attached to us-east-1b
     * To move a volume across, you first need to snapshot it
 * Have a provisioned capacity (size in GBs, and IOPS)
     * You get billed for all the provisioned capacity
     * You can increase the capacity of the drive over time
 
 ### EBS Snapshots ###
 
 * Make a backup  (snapshot) of your EBS Volume at a point in time
 * Not necessary to detach volume to do snapshot, but recommended
 * Can cop snapshot across Avaliablity zone or Region
 * how snap shot works 

   ![Linux Directories](/notes/img/snapshot.png?raw=true "Title")

 * Is possible to copy sanpshot 
 * We can create a new snapshot 

 ### AMI (Amazon Machine Image) ###

 * AMI are customization of an EC2 instance
    * You add your own software, configuration, OS, monitoring
    * Faster boot / configuration time because all your software is pre-packaged
 * AMI are built for a specfic region (and can be copied accross regions)
 * You can launch EC2 instances from 
    * A public AMI:  AWS provided
    * Your own AMI: you make and maintain yourself
    * An AAWS marketplace AMI: an AMI someone else made (and potentially sells)

 ### AMI Process (From an EC2 instance) ###

 * Start an EC2 instance and customize it
 * Stop the instance (for data integirty)
 * Build an AMI - this will also creates EBS snapshots
 * Launch instances from other AMIs

 ### 2. EC2 Instance Store ###
 
 * EBS volumes are network drives with good but “limited” performance
 * If you need a high-performance hardware disk, use EC2 Instance Store
 * Better I/O performance
 * EC2 Instance Store lose their storage if they’re stopped (ephemeral)
 * Good for buffer / cache / scratch data / temporary content
 * Risk of data loss if hardware fails
 * Backups and Replication are your responsibility.

 ### 3. EFS – Elastic File System ###
 
 * Managed NFS (network file system) that can be mounted on 100s of EC2
 * EFS works with Linux EC2 instances in multi-AZ
 * Highly available, scalable, expensive (3x gp2), pay per use, no capacity planning

 #### Shared responsibility  Model for EC2 Storage ####

 ![Linux Directories](/notes/img/sharedec2storage.png?raw=true "Title")

 ## Amazon S3 ##
 
 * Amazon S3 is one of the main building block of AWS
 * It's advertised as "inFinitely scaling" storage
 * Many websites use Amazon S3 as a backbone
 * Many AWS services uses Amazon s3 as an intergration as well 
 * Always recommended to have a step-by-step approach to s3
 * S3 uses 
     * Backup and storage
     * Disaster Recovery
     * Archive
     * Hybrid Cloud storage 
     * Application Hosting
     * Media hosting
     * Data lake & big data analytics 
     * software delivery 
     * Static website
 * In S3 => Buckets - Directories, Object - filies 
  
 ### Amazon S3 Overview - buckets ###

 * Amazon S3 allows people to store objects (files) in buckets (directories)
 * Buckets must have globally unique name (across all region all account)
 * Buckets are defined at the region level 
 * S3 look like a global service but buckets are created in a region
 * Naming convection 
    * No uppercase
    * No underscore
    * 3-63 Character long
    * Not an IP
    * Must start with lowercase letter or number

  ### Amazon S3 Overview - Objects ###
 
 * Objects (files) have a Key 
 * The key is the FULL path: 
     * s3://my-bucket/my_file.txt 
     * s3://my-bucket/my_folder1/another_folder/my_file.txt 
 * The key is composed of prefix + object name 
     * s3://my-bucket/my_folder1/another_folder/my_file.txt 
 * There’s no concept of “directories” within buckets (although the UI will trick you to think otherwise)
 * Just keys with very long names that contain slashes (“/”)
 * Object values are the content of the body:
    * Max Object Size is 5TB (5000GB)
    * If uploading more than 5GB, must use “multi-part upload”
 * Metadata (list of text key / value pairs – system or user metadata)
 * Tags (Unicode key / value pair – up to 10) – useful for security / lifecycle
 * Version ID (if versioning is enabled)

 ### S3 Security ###
 
 * User based 
     * IAM policies - Which API calls should be allowed for a specific user from IAM console
 * Resource based 
     * Bucket poilices - bucket wide rules from the S3 console - allows cross account
     * Object Access Control List (ACL) - finer grain
     * Bucket Access Control Listt (ACl) - Less common
 * Note: an IAM principal can access an S3 object if
     * the user IAM permissions allow it OR the resource policy ALLOWS it
     * AND there’s no explicit DENY
 * Encryption: encrypt objects in Amazon S3 using encryption keys

  ### S3 Bucket Policies ###
 
 * JSON based policies 
     * Resources: buckets and objects 
     * Actions: Set of API to Allow or Deny 
     * Effect: Allow / Deny 
     * Principal: The account or user to apply
       the policy to
 * Use S3 bucket for policy to: 
     * Grant public access to the bucket 
     * Force objects to be encrypted at upload 
     * Grant access to another account (Cross Account)

 ### S3 Websites ###

 * S3 can host static websites and have them accessible on the www
 * The website URL will be:
     * <bucket-name>.s3-website-<AWS-region>.amazonaws.com
     OR
     * <bucket-name>.s3-website.<AWS-region>.amazonaws.com

 * If we get a 403 (Forbidden) error, make sure the bucket policy allows
   public reads!

 ### Amason S3 - Versioning ### 
 
 * You can version your files in Amazon S3
 * It is enabled at the bucket level
 * Same key overwrite will increment the “version”: 1, 2, 3….
 * It is best practice to version your buckets
    * Protect against unintended deletes (ability to restore a version)
    * Easy roll back to previous version
 * Notes:
    * Any file that is not versioned prior to enabling versioning will have version “null”
    * Suspending versioning does not delete the previous versions

 ### S3 Access logs ###

 * For audit purpose, you may want to log all access to S3 buckets
 * Any request made to S3, from any account, authorized or denied, will be logged into another S3 bucket
 * That data can be analyzed using data analysis tools…
 * Very helpful to come down to the root cause of an issue, or audit usage, view suspicious patterns, etc… 

 ### S3 Replication (CRR & SRR) ### 

 * Must enable versioning in source and destination
 * Cross Region Replication (CRR)
 * Same Region Replication (SRR)
 * Buckets can be in different accounts
 * Copying is asynchronous
 * Must give proper IAM permissions to S3
 * CRR - Use cases: compliance, lower latency access, replication across accounts
 * SRR – Use cases: log aggregation, live replication between production and test accounts

 ### S3 Storage Classes ###
 
 1. Amazon S3 Standard - General Purpose
 2. Amazon S3 Standard-Infrequent Access (IA)
 3. Amazon S3 One Zone-Infrequent Access
 4. Amazon S3 Intelligent Tiering
 5. Amazon Glacier
 6. Amazon Glacier Deep Archive
 7. Amazon S3 Reduced Redundancy Storage (deprecated - omitted)

 ### S3 Durability and Availability ###

 * Durability:
    * High durability (99.999999999%, 11 9’s) of objects across multiple AZ
    * If you store 10,000,000 objects with Amazon S3, you can on average expect to incur a loss of a single object once every 10,000 years
    * Same for all storage classes
 * Availability:
    * Measures how readily available a service is
    * S3 standard has 99.99% availability, which means it will not be available 53 minutes a year
 * Varies depending on storage class

 ### S3 Standard – General Purposes ###
 
 * 99.99% Availability
 * Used for frequently accessed data
 * Low latency and high throughput
 * Sustain 2 concurrent facility failures
 * Use Cases: Big Data analytics, mobile & gaming applications, content

 ### S3 Standard – Infrequent Access (IA) ###

 * Suitable for data that is less frequently accessed, but requires rapid access when needed
 * 99.9% Availability
 * Lower cost compared to Amazon S3 Standard, but retrieval fee
 * Sustain 2 concurrent facility failures
 * Use Cases: As a data store for disaster recovery, backups…

 ### S3 Intelligent-Tiering ###

 * 99.9% Availability
 * Same low latency and high throughput performance of S3 Standard
 * Cost-optimized by automatically moving objects between two access tiers based on changing access patterns:
 * Frequent access
 * Infrequent access
 * Resilient against events that impact an entire Availability Zone

 ### S3 One Zone - Infrequent Access (IA) ###

 * Same as IA but data is stored in a single AZ
 * 99.5% Availability
 * Low latency and high throughput performance
 * Lower cost compared to S3-IA (by 20%)
 * Use Cases: Storing secondary backup copies of on-premise data, or storing data you can recreate

 ### Amazon Glacier & Glacier Deep Archive ###

 * Low cost object storage (in GB/month) meant for archiving / backup
 * Data is retained for the longer term (years)
 * Various retrieval options of time + fees for retrieval:
 * Amazon Glacier – cheap:
    * Expedited (1 to 5 minutes)
    * Standard (3 to 5 hours)
    * Bulk (5 to 12 hours)
 * Amazon Glacier Deep Archive – cheapest:
    * Standard (12 hours)
    * Bulk (48 hours)

 ### S3 Storage Classes Comparison ###
 
 ![Linux Directories](/notes/img/com.png?raw=true "Title")

 ## Databases ##

 * Storing data on disk (EFS, EBS, EC2 Instance Store, S3) can have its limits
 * Sometimes, you want to store data in a database…
 * We can structure the data
 * We build indexes to efficiently query / search through the data
 * We define relationships between your datasets
 * Databases are optimized for a purpose and come with different features, shapes and constraints 
 
 ### Relational Databases ###
  
 * Looks just like Excel Spreadsheets, with links b/w them.
 * Can use the SQL language to perform queries / lookups

  ### NoSQL Databases ###
 
 * NoSQL = non-SQL = non relational databases
 * NoSQL databases are purpose built for specific data models and have flexible schemas for building modern applications.
 * Benefits:
    * Flexibility: easy to evolve data model
    * Scalability: designed to scale-out by using distributed clusters
    * High-performance: optimized for a specific data model
    * Highly functional: types optimized for the data model
 * Examples: Key-value, document, graph, in-memory, search databases
 * NoSQL data example: JSON
     * JSON = JavaScript Object Notation, common form of data that fits into a NoSQL model
     * Data can be nested, Fields can change oover time
 
 ### 1. AWS RDS Overview ###

 * RDS stands for Relational Database Service
 * It’s a managed DB service for DB use SQL as a query language.
 * It allows you to create databases in the cloud that are managed by AWS
     1. Postgres
     2. MySQL
     3. MariaDB
     4. Oracle
     5. Microsoft SQL Server
     6. Aurora (AWS Proprietary database)
 * Advantage using RDS
     * Automated provisioning, OS patching
     * Continuous backups and restore to specific timestamp (Point in Time Restore)!
     * Monitoring dashboards
     * Read replicas for improved read performance
     * Multi AZ setup for DR (Disaster Recovery)
     * Maintenance windows for upgrades
     * Scaling capability (vertical and horizontal)
     * Storage backed by EBS (gp2 or io1)
 * BUT you can’t SSH into your instances

 ### 2. Amazon Aurora ###

 * Aurora is a proprietary technology from AWS (not open sourced)
 * PostgreSQL and MySQL are both supported as Aurora DB
 * Aurora is “AWS cloud optimized” and claims 5x performance improvement over MySQL on RDS, over 3x the performance of Postgres on RDS
 * Aurora storage automatically grows in increments of 10GB, up to 64 TB.
 * Aurora costs more than RDS (20% more) – but is more efficient
 * Not in the free tier

 ### 3. Amazon ElastiCache Overview ####

 * The same way RDS is to get managed Relational Databases…
 * ElastiCache is to get managed Redis or Memcached
 * Caches are in-memory databases with high performance, low latency
 * Helps reduce load off databases for read intensive workloads
 * AWS takes care of OS maintenance / patching, optimizations, setup, configuration, monitoring, failure recovery and backups
 
  ![Linux Directories](/notes/img/elasticache.png?raw=true "Title")

 ### 4.Dynamo DB ###

 * Fully Managed Highly available with replication across 3 AZ
 * NoSQL database - not a relational database
 * Scales to massive workloads, distributed “serverless” database
 * Millions of requests per seconds, trillions of row, 100s of TB of storage
 * Fast and consistent in performance
 * Single-digit millisecond latency – low latency retrieval
 * Integrated with IAM for security, authorization and administration
 * Low cost and auto scaling capabilities

  ![Linux Directories](/notes/img/dynamoDB.png?raw=true "Title")

 ### 5.Redshift Overview ### 

 * Redshift is based on PostgreSQL, but it’s not used for OLTP
 * It’s OLAP – online analytical processing (analytics and data warehousing)
 * Load data once every hour, not every second
 * 10x better performance than other data warehouses, scale to PBs of data
 * Columnar storage of data (instead of row based)
 * Massively Parallel Query Execution (MPP), highly available
 * Pay as you go based on the instances provisioned
 * Has a SQL interface for performing the queries
 * BI tools such as AWS Quicksight or Tableau integrate with it

 ### 6.Amazon EMR ###

 * EMR stands for “Elastic MapReduce”
 * EMR helps creating Hadoop clusters (Big Data) to analyze and process vast amount of data
 * The clusters can be made of hundreds of EC2 instances
 * Also supports Apache Spark, HBase, Presto, Flink…
 * EMR takes care of all the provisioning and configuration
 * Auto-scaling and integrated with Spot instances
 * Use cases: data processing, machine learning, web indexing, big data…

 ### Athena Overview ###

 * Fully Serverless database with SQL capabilities
 * Used to query data in S3
 * Pay per query
 * Output results back to S3
 * Secured through IAM
 * Use Case: one-time SQL queries, serverless queries on S3, log analytics.

 ### AWS Glue ###

 * Managed extract, transform, and load (ETL)    
 * Useful to prepare and transform data for analytics 
 * Fully serverless service 
 * Glue Data Catalog: catalog of datasets 
 * can be used by Athena, Redshift, EMR
 
 ### DMS – Database Migration Service ###

 • Quickly and securely migrate databases to AWS, resilient, self healing
 • The source database remains available during the migration
 • Supports:
    • Homogeneous migrations: ex Oracle to Oracle
    • Heterogeneous migrations: ex Microsoft SQL Server to Aurora

 ## Docker ##

 * Docker is a software development platform to deploy apps 
 * Apps are packaged in containers that can be run on any OS 
 * Apps run the same, regardless of where they’re run
     * Any machine 
     * No compatibility issues 
     * Predictable behavior 
     * Less work 
     * Easier to maintain and deploy 
     * Works with any language, any OS, any technology 
 * Scale containers up and down very quickly (seconds)
 * Docker images are stored in Docker Repositories • Public: Docker Hub https://hub.docker.com/ 
 * Find base images for many technologies or OS: 
    * Ubuntu  
    * MySQL 
    * NodeJS, Java…
 * Docker is ”sort of” a virtualization technology, but not exactly
 * Resources are shared with the host => many containers on one server

 ![Linux Directories](/notes/img/docker.png?raw=true "Title")

 ## ECS (Elastic Container Service) ##

 * Launch Docker containers on AWS
 * You must provision & maintain the infrastructure (the EC2 instances)
 * AWS takes care of starting / stopping containers
 * Has integrations with the Application Load Balancer

 ## Fargate ##

 * Launch Docker containers on AWS
 * You do not provision the infrastructure (no EC2 instances to manage) – simpler!
 * Serverless offering 
 * AWS just runs containers for you based on the CPU / RAM you need.

 ## ECR (Elastic Container Registry) ##

 * Private Docketr Registry on AWS
 * This is where we store Docker images so they can be run by ECS or fagate

 ## What’s serverless? ##

 * Serverless is a new paradigm in which the developers don’t have to manage servers anymore…
 * They just deploy code
 * They just deploy… functions !
 * Initially... Serverless == FaaS (Function as a Service)
 * Serverless was pioneered by AWS Lambda but now also includes anything that’s managed: “databases, messaging, storage, etc.”
 * Serverless does not mean there are no servers… it means you just don’t manage / provision / see them

 ## Lambda vs EC2 ## 
 
 * EC2 
    * Virtual Servers in the Cloud
    * Limited by RAM and CPU
    * Continuously running
    * Scaling means intervention to add / remove servers
 * Amazon Lambda
    * Virtual functions – no servers to manage!
    * Limited by time - short executions
    * Run on-demand
    * Scaling is automated!

 ## AWS Lambda ##
 
 * Easy Pricing:
 * Pay per request and compute time
 * Free tier of 1,000,000 AWS Lambda requests and 400,000 GBs of compute time
 * Integrated with the whole AWS suite of services
 * Event-Driven: functions get invoked by AWS when needed
 * Integrated with many programming languages
 * Easy monitoring through AWS CloudWatch
 * Easy to get more resources per functions (up to 3GB of RAM!)
 * Increasing RAM will also improve CPU and network! 

 * AWS Lambda language support 
     * Node.js (JavaScript) 
     * Python 
     * Java (Java 8 compatible) 
     * C# (.NET Core) 
     * Golang 
     * C# / Powershell 
     * Ruby 
     * Custom Runtime API (community supported, example Rust) 
     * Important: Docker is not for AWS Lambda, it’s for ECS / Fargate 


 ### AWS Lambda Pricing: example ###
 * You can find overall pricing information here: https://aws.amazon.com/lambda/pricing/
 * Pay per calls:
    * First 1,000,000 requests are free 
    * $0.20 per 1 million requests thereafter ($0.0000002 per request)
 * Pay per duration: (in increment of 100ms) 
    * 400,000 GB-seconds of compute time per month if FREE 
    * == 400,000 seconds if function is 1GB RAM 
    * == 3,200,000 seconds if function is 128 MB RAM 
    * After that $1.00 for 600,000 GB-seconds 
 * It is usually very cheap to run AWS Lambda so it’s very popular.

 ### AWS Batch ###
 * Fully managed batch processing at any scale
 * Efficiently run 100,000s of computing batch jobs on AWS
 * A “batch” job is a job with a start and an end (opposed to continuous)
 * Batch will dynamically launch EC2 instances or Spot Instances
 * AWS Batch provisions the right amount of compute / memory
 * You submit or schedule batch jobs and AWS Batch does the rest!
 * Batch jobs are defined as Docker images and run on ECS
 * Helpful for cost optimizations and focusing less on the infrastructure

 ### Batch vs Lambda ###

 • Lambda: 
   • Time limit 
   • Limited runtimes 
   • Limited temporary disk space 
   • Serverless 
 • Batch: 
   • No time limit 
   • Any runtime as long as it’s packaged as a Docker image 
   • Rely on EBS / instance store for disk space 
   • Relies on EC2 (can be managed by AWS)

 ### Amazon Lightsail ###

 * Virtual servers, storage, databases, and networking
 * Low & predictable pricing
 * Simpler alternative to using EC2, RDS, ELB, EBS, Route 53…
 * Great for people with little cloud experience!
 * Can setup notifications and monitoring of your Lightsail resources
 * Use cases:
    * Simple web applications (has templates for LAMP, Nginx, MEAN, Node.js…)
    * Websites (templates for WordPress, Magento, Plesk, Joomla)
    * Dev / Test environment
 * Has high availability but no auto-scaling, limited AWS integrations


 ### Other Compute - Summary ###

 * Docker: container technology to run applications
 * ECS: run Docker containers on EC2 instances
 * Fargate:
    * Run Docker containers without provisioning the infrastructure
    * Serverless offering (no EC2 instances)
 * ECR: Private Docker Images Repository
 * Batch: run batch jobs on AWS across managed EC2 instances
 * Lightsail: predictable & low pricing for simple application & DB stacks

 ## Deploying and Managing Infrastructure at Scale Section ##

 ## What is CloudFormation ##

 * CloudFormation is a declarative way of outlining your AWS Infrastructure, for any resources (most of them are supported).
 * For example, within a CloudFormation template, you say:
   * I want a security group
   * I want two EC2 instances using this security group
   * I want an S3 bucket
   * I want a load balancer (ELB) in front of these machines
 * Then CloudFormation creates those for you, in the right order, with the exact configuration that you specify

 ### Benefits of AWS CloudFormation ###
 * Infrastructure as code
    * No resources are manually created, which is excellent for control
    * Changes to the infrastructure are reviewed through code
 * Cost
   * Each resources within the stack is tagged with an identifier so you can easily see how much a stack costs you
   * You can estimate the costs of your resources using the CloudFormation template
   * Savings strategy: In Dev, you could automation deletion of templates at 5 PM and recreated at 8 AM, safely
 * Productivity
   * Ability to destroy and re-create an infrastructure on the cloud on the fly
   * Automated generation of Diagram for your templates!
   * Declarative programming (no need to figure out ordering and orchestration)
 * Don’t re-invent the wheel
   * Leverage existing templates on the web!
   * Leverage the documentation
 * Supports (almost) all AWS resources:
   * Everything we’ll see in this course is supported
   * You can use “custom resources” for resources that are not supported

 ### Developer problems on AWS ###
 * Managing infrastructure
 * Deploying Code
 * Configuring all the databases, load balancers, etc
 * Scaling concerns
 * Most web apps have the same architecture (ALB + ASG)
 * All the developers want is for their code to run!
 * Possibly, consistently across different applications and environments

 ### AWS Elastic Beanstalk Overview ###
 * Elastic Beanstalk is a developer centric view of deploying an application on AWS
 * It uses all the component’s we’ve seen before: EC2, ASG, ELB, RDS, etc…
 * But it’s all in one view that’s easy to make sense of! 
 * We still have full control over the configuration 
 * Beanstalk = Platform as a Service (PaaS) 
 * Beanstalk is free but you pay for the underlying instances

 ### Elastic Beanstalk ###
 * Managed service
   * Instance configuration / OS is handled by Beanstalk
   * Deployment strategy is configurable but performed by Elastic Beanstalk
 * Just the application code is the responsibility of the developer
 * Three architecture models:
   * Single Instance deployment: good for dev
   * LB + ASG: great for production or pre-production web applications
   * ASG only: great for non-web apps in production (workers, etc..)

 ### Elastic Beanstalk ###

 * Support for many platforms:
   * Go
   * Java SE
   * Java with Tomcat
   * .NET on Windows Server with IIS
   * Node.js
   * PHP
   * Python
   * Ruby
   * Packer Builder

 ### AWS CodeDeploy ###

 * We want to deploy our application automatically
 * Works with EC2 Instances
 * Works with On-Premises Servers
 * Hybrid service
 * Servers / Instances must be provisioned and configured ahead of time with the CodeDeploy Agent

 ### AWS Systems Manager (SSM) ###
 * Helps you manage your EC2 and On-Premises systems at scale
 * Another Hybrid AWS service
 * Get operational insights about the state of your infrastructure
 * Suite of 10+ products
 * Most important features are:
    * Patching automation for enhanced compliance
    * Run commands across an entire fleet of servers
    * Store parameter configuration with the SSM Parameter Store
 * Works for both Windows and Linux OS

 ### How Systems Manager works ###

 * We need to install the SSM agent onto the systems we control
 * Installed by default on Amazon Linux AMI & some Ubuntu AMI
 * If an instance can’t be controlled with SSM, it’s probably an issue with the SSM agent!
 * Thanks to the SSM agent, we can run commands, patch & configure our servers

 ### AWS OpsWorks ### 

 * Chef & Puppet help you perform server configuration automatically, or repetitive actions
 * They work great with EC2 & On-Premises VM
 * AWS OpsWorks = Managed Chef & Puppet
 * It’s an alternative to AWS SSM
 * Only provision standard AWS resources:
    * EC2 Instances, Databases, Load Balancers, EBS volumes…
 * In the exam: Chef or Puppet needed => AWS OpsWorks

 ![Linux Directories](/notes/img/ops.png?raw=true "Title")

 ## Global Infrastructure Section ##

 ### Why make a global application? ###

 * A global application is an application deployed in multiple geographies
 * On AWS: this could be Regions and / or Edge Locations
 * Decreased Latency
   * Latency is the time it takes for a network packet to reach a server
   * It takes time for a packet from Asia to reach the US
   * Deploy your applications closer to your users to decrease latency, better experience
 * Disaster Recovery (DR)
   * If an AWS region goes down (earthquake, storms, power shutdown, politics)…
   * You can fail-over to another region and have your application still working
   * A DR plan is important to increase the availability of your application
 * Attack protection: distributed global infrastructure is harder to attack 


 ### Global Applications in AWS ###
 * Global DNS: Route 53
   * Great to route users to the closest deployment with least latency
   * Great for disaster recovery strategies
 * Global Content Delivery Network (CDN): CloudFront
   * Replicate part of your application to AWS Edge Locations – decrease latency
   * Cache common requests – improved user experience and decreased latency
 * S3 Transfer Acceleration
   * Accelerate global uploads & downloads into Amazon S3
 * AWS Global Accelerator:
   * Improve global application availability and performance using the AWS global network


 ### Amazon Route 53 Overview ###

 * Route53 is a Managed DNS (Domain Name System)
 * DNS is a collection of rules and records which helps clients understand how to reach a server through URLs.
 * In AWS, the most common records are:
   * www.google.com => 12.34.56.78 == A record (IPv4)
   * www.google.com => 2001:0db8:85a3:0000:0000:8a2e:0370:7334 == AAAA IPv6
   * search.google.com => www.google.com == CNAME: hostname to hostname
   * example.com => AWS resource == Alias (ex: ELB, CloudFront, S3, RDS, etc…)

 ### AWS CloudFront ###
 * Content Delivery Network (CDN)
 * Improves read performance, content is cached at the edge
 * Improves users experience
 * 216 Point of Presence globally (edge locations)
 * DDoS protection (because worldwide), integration with Shield, AWS Web Application Firewall

 ### CloudFront – Origins ###

 * S3 bucket 
     * For distributing files and caching them at the edge 
     * Enhanced security with CloudFront Origin Access Identity (OAI) 
     * CloudFront can be used as an ingress (to upload files to S3) 
 * Custom Origin (HTTP) 
     * Application Load Balancer 
     * EC2 instance 
     * S3 website (must first enable the bucket as a static S3 website) 
     * Any HTTP backend you want

 ### CloudFront vs S3 Cross Region Replication ###

 * CloudFront:
    * Global Edge network
    * Files are cached for a TTL (maybe a day)
    * Great for static content that must be available everywhere
 * S3 Cross Region Replication:
    * Must be setup for each region you want replication to happen
    * Files are updated in near real-time
    * Read only
    * Great for dynamic content that needs to be available at low-latency in few regions

 ### S3 Transfer Acceleration ###

 * Increase transfer speed by transferring file to an AWS edge location which will forward the data to the S3 bucket in the target region S3 Bucket
 * Test the tool at: https://s3-accelerate-speedtest.s3-accelerate.amazonaws.com/en/accelerate-speed-comparsion.html

 ### AWS Global Accelerator ###
 * Improve global application availability and performance using the AWS global network
 * Leverage the AWS internal network to optimize the route to your application (60% improvement)
 * 2 Anycast IP are created for your application and traffic is sent through Edge Locations
 * The Edge locations send the traffic to your application

 ### AWS Global Accelerator vs CloudFront ###

 * They both use the AWS global network and its edge locations around the world
 * Both services integrate with AWS Shield for DDoS protection.
 * CloudFront – Content Delivery Network
    * Improves performance for your cacheable content (such as images and videos)
    * Content is served at the edge
 * Global Accelerator
    * No caching, proxying packets at the edge to applications running in one or more AWS Regions.
    * Improves performance for a wide range of applications over TCP or UDP
    * Good for HTTP use cases that require static IP addresses
    * Good for HTTP use cases that required deterministic, fast regional failover


 ## Cloud Integration Section ##

 * When we start deploying multiple applications, they will inevitably need to communicate with one another
 * There are two patterns of application communication
 * Synchronous between applications can be problematic if there are sudden spikes of traffic
 * What if you need to suddenly encode 1000 videos but usually it’s 10?
 * In that case, it’s better to decouple your applications:
   * using SQS: queue model
   * using SNS: pub/sub model
   * using Kinesis: real-time data streaming model (out of scope for the exam)
 * These services can scale independently from our application!

 ### Amazon SQS – Standard Queue ###

 * Oldest AWS offering (over 10 years old)
 * Fully managed service (~serverless), use to decouple applications
 * Scales from 1 message per second to 10,000s per second
 * Default retention of messages: 4 days, maximum of 14 days
 * No limit to how many messages can be in the queue
 * Messages are deleted after they’re read by consumers
 * Low latency (<10 ms on publish and receive)
 * Consumers share the work to read messages & scale horizontally

 ### Amazon SNS ###

 * The “event publishers” only sends message to one SNS topic
 * As many “event subscribers” as we want to listen to the SNS topic notifications
 * Each subscriber to the topic will get all the messages
 * Up to 10,000,000 subscriptions per topic, 100,000 topics limit
 * SNS Subscribers can be:
    * HTTP / HTTPS (with delivery retries – how many times)
    * Emails, SMS messages, Mobile Notifications
    * SQS queues (fan-out pattern), Lambda Functions (write-your-own integration)

 ## Cloud Monitoring Section ##

 ### Amazon CloudWatch Metrics ###
 
 * CloudWatch provides metrics for every services in AWS
 * Metric is a variable to monitor (CPUUtilization, NetworkIn…)
 * Metrics have timestamps
 * Can create CloudWatch dashboards of metrics

 ### Important Metrics ###

 * EC2 instances: CPU Utilization, Status Checks, Network (not RAM)
    * Default metrics every 5 minutes
    * Option for Detailed Monitoring ($$$): metrics every 1 minute
 * EBS volumes: Disk Read/Writes
 * S3 buckets: BucketSizeBytes, NumberOfObjects, AllRequests
 * Billing:Total Estimated Charge (only in us-east-1)
 * Service Limits: how much you’ve been using a service API
 * Custom metrics: push your own metrics

 ### Amazon CloudWatch Alarms ###

 * Alarms are used to trigger notifications for any metric
 * Alarms actions…
       * Auto Scaling: increase or decrease EC2 instances “desired” count
       * EC2 Actions: stop, terminate, reboot or recover an EC2 instance
       * SNS notifications: send a notification into an SNS topic
 * Various options (sampling, %, max, min, etc…)
 * Can choose the period on which to evaluate an alarm
 * Example: create a billing alarm on the CloudWatch Billing metric
 * Alarm States: OK. INSUFFICIENT_DATA, ALARM

 ### Amazon CloudWatch Logs ###
 
 * CloudWatch Logs can collect log from: 
     * Elastic Beanstalk: collection of logs from application 
     * ECS: collection from containers 
     * AWS Lambda: collection from function logs 
     * CloudTrail based on filter • CloudWatch log agents: on EC2 machines or on-premises servers • Route53: Log DNS queries • Enables real-time monitoring of logs • Adjustable CloudWatch Logs retention

 ### CloudWatch Logs for EC2 ###

 * By default, no logs from your EC2 instance will go to CloudWatch
 * You need to run a CloudWatch agent on EC2 to push the log files we want
 * Make sure IAM permissions are correct
 * The CloudWatch log agent can be setup on-premises too EC2 Instance

 ### Amazon CloudWatch Events ###

 * Schedule: Cron jobs (scheduled scripts)
 * Event Pattern: Event rules to react to a service doing something
 * Trigger Lambda functions, send SQS/SNS messages…

 ### Amazon EventBridge ###

 * EventBridge is the next evolution of CloudWatch Events
 * Default event bus: generated by AWS services (CloudWatch Events)
 * Partner event bus: receive events from SaaS service or applications (Zendesk, DataDog, Segment, Auth0…)
 * Custom Event buses: for your own applications
 * Schema Registry: model event schema
 * EventBridge has a different name to mark the new capabilities
 * The CloudWatch Events name will be replaced with EventBridge

 ### AWS CloudTrail ###

 * Provides governance, compliance and audit for your AWS Account
 * CloudTrail is enabled by default!
 * Get an history of events / API calls made within your AWS Account by:
    * Console
    * SDK
    * CLI
    * AWS Services
 * Can put logs from CloudTrail into CloudWatch Logs or S3
 * A trail can be applied to All Regions (default) or a single Region.
 * If a resource is deleted in AWS, investigate CloudTrail first!


 ### AWS X-Ray ###
 
 * Debugging in Production, the good old way:
    * Test locally
    * Add log statements everywhere
    * Re-deploy in production
 * Log formats differ across applications and log analysis is hard.
 * Debugging: one big monolith “easy”, distributed services “hard”
 * No common views of your entire architecture
 * Enter… AWS X-Ray!

 ### AWS Status - Service Health Dashboard ###

 * Shows all regions, all services health
 * Shows historical information for each day
 * Has an RSS feed you can subscribe to
 * https://status.aws.amazon.com/

 ### AWS Personal Health Dashboard ###

 * AWS Personal Health Dashboard provides alerts and remediation guidance when AWS is experiencing events that may impact you.
 * While the Service Health Dashboard displays the general status of AWS services, Personal Health Dashboard gives you a personalized view into the performance and availability of the AWS services underlying your AWS resources.
 * The dashboard displays relevant and timely information to help you manage events in progress and provides proactive notification to help you plan for scheduled activities. 

 ### AWS Personal Health Dashboard ###

 * Global service https://phd.aws.amazon.com/ 
 * Shows how AWS outages directly impact you & your AWS resources
 * Alert, remediation, proactive, scheduled activities

 ### Monitoring Summary ###

 * CloudWatch:
     * Metrics: monitor the performance of AWS services and billing metrics
     * Alarms: automate notification, perform EC2 action, notify to SNS based on metric
     * Logs: collect log files from EC2 instances, servers, Lambda functions…
     * Events (or EventBridge): react to events in AWS, or trigger a rule on a schedule
 * CloudTrail: audit API calls made within your AWS account
 * X-Ray: trace requests made through your distributed applications
 * Service Health Dashboard: status of all AWS services across all regions
 * Personal Health Dashboard: AWS events that impact your infrastructure
