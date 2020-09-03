 # AWS Cloud practitioner exam # 

 ## Table of contents ##
 1. What is Cloud Computing 
 2. IAM - Identity and Access Management


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

 