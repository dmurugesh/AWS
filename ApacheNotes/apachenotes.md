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