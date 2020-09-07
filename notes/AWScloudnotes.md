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

 
