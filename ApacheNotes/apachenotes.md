 # Apache Notes #

 ## Apache Introduction ##
 
 * Apache is an open-source and free web server software that powers around 40% of websites around the world. The official name is Apache HTTP Server, and it’s maintained and developed by the Apache Software Foundation.
 * It allows website owners to serve content on the web — hence the name “web server.” It’s one of the oldest and most reliable web servers, with the first version released more than 20 years ago, in 1995.
 * Apache is one of the most popular web servers that allows you to run a secure website without too much of a headache. It’s the most frequent choice of solopreneurs and small businesses that want a presence on the web.

 ## Apache Pros and Cons ##

 * An Apache web server can be an excellent choice to run your website on a stable and versatile platform. However, it also comes with some disadvantages you need to pay attention to.

 Pros:
   * Open-source and free, even for commercial use.
   * Reliable, stable software.
   * Frequently updated, regular security patches.
   * Flexible due to its module-based structure.
   * Easy to configure, beginner-friendly.
   * Cross-platform (works on both Unix and Windows servers).
   * Works out of the box with WordPress sites.
   * Huge community and easily available support in case of any problem.

 Cons:
   * Performance problems on extremely traffic-heavy websites.
   * Too many configuration options can lead to security vulnerabilities.

 ## How to Install Apache in CentOS ##

 ```
   yum install httpd       -- This command is used to install apache
   systemctl start httpd   -- Used to start apache server
   systemctl enable httpd  -- Used to enable apched automatic once you on your system
 ```
 
  ## Command used to configure firewall service ##

 ```
 1. firewall -cmd --permanent --add-service=http 
 2. firewall -cmd --permanent --add-service=https  => provide access to port 80 or port 443  
 3. firewall -cmd --reload

 ```
 * other commands of apache 
 ```
  whereis httpd   --- find all the files location related to httpd
  httpd -l        --- Gives the list of modules in httpd 
  httpd -M        --- Gives the list of all modules associated with httpd 
  httpd -t -f /etc/httpd/conf/httpd.conf  --- to make modifications on the apache configuration 
 
 ```
 
 ## directories ##
 ```
 /etc/httpd         --- has the custom config file
 /var/log/httpd     --- contains the log files 
 /usr/lib64/httpd  --- modules of appache 

 ```
 
  ## Virtual Host ##

 * Virtual host helps us to create multiple website on same webserver
 #### Virtual Host by name / Name based Virtual Hosting ####
    * Multiple websites on same IP Address
    * NameViertualHost x.x.x.x inhttpd.conf
 #### IPbased Virtual Hosting ####
    * Each website has its own dedicated IP address
    * Single site can have multiple IP addresses

 #### Creating name based virtual host ####
 * cd /etc/httpd/conf.d
 * nano conf.d
 * <VirtualHost *:80> ServerName: DocumentRoot:
 * httpd -t - to check the configuration is correct 
 * systemctl reload httpd

#### Creating port based virtual Host ####
 * cd/etc/httpd/conf.d
 * nano conf.d
 * Listen 8080 <VirtualHost *:8080> DocumentRoot "path" ServerName <>
 * httpd -t - to check the configuration is correct 
 * systemctl reload httpd 
 * firewall-cmd --permanent --add-port=/tcp - to allow the port 
 * firewall-cmd --reload 8. sudo firewall-cmd --list-all - to view opened ports

 ## Alias ##

 * Using Alias we can upload theimages for website/URL from another location. 
 * Use Alias inside the configuration file 
   ```
    Alias <foldername> <exactFile location>
  
      eg: Alias /img /var/www/html/images
   ```
 * 

 ## Redirecting ##

 * When we change the website to another location/site we  also need users to redirect to new page as well
 * 4 redirecting types
      * permanent -- Tells the users that our resources has moved permanently, Status code 310
      * temp      -- Tells the user that our resources has moved temporally, status code 300
      * seeother  -- Tells the user that required resoures is replaced by another one, status code 393
      * gone      -- Tells the user that the resources they are looking for move to permanently, status code 410

 ## Node Js ##

 * An Open source , runtime enviroment for excuting Javascript Code outside browser
 * Use for backend service
 * Ideal for building Highly-scable, data-intensive and real time aps
 * Advantages
     * Great for protopying and agile development 
     * Superfast and highly scalable 
     * Javascript Everywhere
     * Cleaner and more consistent codebase 
     * Large ecosystem of open-source libs
 * 
 
  ## Apache Logging Facilities ##

 * Apache can produce many types of logs. The two essential types are the access log, where all requests are noted, and the error log, which is designed to log various informational and debug messages, plus every exceptional event that occurs. Additional information can be found in module-specific logs, as is the case with mod_ssl, mod_rewrite and mod_security. The access log is created and written to by the module mod_log_config, which is not a part of the core, but this module is so important that everyone treats it as if it is.
 #### Request Logging ####
 * You only need to be familiar with three configuration directives to manage request logging:
     * LogFormat
     * transferLog
     * CustomLog
 * In fact, you will need to use only two. The CustomLog directive is so flexible and easy to use that you will rarely need to use transferLog in your configuration. (It will become clear why later.)
 * Other directives are available, but they are deprecated and should not be used because CustomLog can achieve all the necessary functionality. Some have been removed from Apache 2:

 #### LogFormat ####
 * Before covering the process of logging to files, consider the format of our log files. One of the benefits of Apache is its flexibility when it comes to log formatting. All this is owed to the LogFormat directive, whose default is the following, referred to as the Common Log Format (CLF):
 * LogFormat "%h %l %u %t \"%r\" %>s %b" common
 * The first parameter is a format string indicating the information to be included in a log file and the format in which it should be written; the second parameter gives the format string a name. You can decipher the log format using the symbol table. The table is available from the Apache reference documentation (http://httpd.apache.org/docs-2.0/mod/mod_log_config.html). It is reproduced in Table 8-1.

 #### CustomLog ####
 * The real power comes from using the CustomLog directive. The equivalent to the transferLog usage described above looks like this:
 * CustomLog /var/www/logs/access_log custom
 * The explicit naming of the log format helps us avoid mistakes. I like this directive because of its conditional logging features. Have a look at the following configuration fragment:

