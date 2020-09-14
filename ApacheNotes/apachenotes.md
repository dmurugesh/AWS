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
 
 
 The Apache HTTP Server Project uses Subversion for hosting its source code.

To check out the 2.4.x branch:

svn checkout http://svn.apache.org/repos/asf/httpd/httpd/branches/2.4.x httpd-2.4.x

To check out the current development version (as of this writing, 2.5.x), use:

svn checkout http://svn.apache.org/repos/asf/httpd/httpd/trunk httpd-trunk

Committers should check out via https instead of http (so that they can commit their changes). For more info about Subversion, please read the ASF version control FAQ.

The developers continue to seek to maintain module compatibility between 2.4.1 and future 2.4 releases for administrators and end users.

Maintaining the Sources
Almost all files relating to Apache, both the actual sources and the files that aren't part of the distribution, are now maintained in an SVN repository. Here is the way in which changes are applied:

Developer checks out a copy of the files on which they want to work (in this case, the trunk), into a private working directory called httpd-trunk:
% svn checkout http://svn.apache.org/repos/asf/httpd/httpd/trunk httpd-trunk
This step only needs to be performed once (unless the private working directory is tainted or deleted). Committers should use a URL prefix of https on the checkout, to save themselves headaches later.

Developer keeps their working directory synchronised with changes made to the repository:
% svn update httpd-trunk
This should probably be done daily or even more frequently during periods of high activity.

Developer makes changes to their working copies, makes sure they work, and generates a patch so others can apply the changes to test them:
% svn diff httpd-trunk/modules/http/mod_mime.c > /tmp/foo
The /tmp/foo file is mailed to the developers list so they can consider the value/validity of the patch. It is worth making sure your code follows the Apache style, as described in the style guide.

Once other developers have agreed that the change is a Good Thing, the developer checks the changes into the repository:
% svn commit httpd-trunk/modules/http/mod_mime.c
SVN Subtrees
There are several different branches under the httpd subtree in the Apache SVN repository that pertain to the different releases. The top level can be perused with the SVN ViewCVS pages. The main subtrees pertaining to the httpd server source are:

httpd-2.4
To create a directory tree containing the 2.4 sources, and call it httpd-2.4, change your current directory to the parent of the tree and then check the 2.4 sources out as follows:

% cd /usr/local/apache
% svn checkout http://svn.apache.org/repos/asf/httpd/httpd/branches/2.4.x httpd-2.4
httpd-2.5
If you want to check out the bleeding edge of development, the httpd-2.5 development tree (slated for a release 2.6), and call it httpd-trunk, checkout as follows:

% cd /usr/local/apache
% svn checkout http://svn.apache.org/repos/asf/httpd/httpd/trunk httpd-trunk
httpd-site
This subtree contains the files that live at http://httpd.apache.org/. The directory on the host that maps to that URL is actually a set of checked-out working copies of the SVN files.

Basic changes can be made to this website in your browser by using the ASF CMS system.

First, add this as a bookmark:

    javascript:void(location.href='https://cms.apache.org/redirect?uri='+escape(location.href))

Then browse to the page you'd like to edit, and click the CMS bookmark. The CMS system allows you to edit, commit, preview in staging, then push to production from a browser interface.

The SVN URL is https://svn.apache.org/repos/asf/httpd/site/trunk/docs. It is important that the files on the Web host not be modified directly. If you want or need to change one, check it out into a private working copy, modify that , commit the change into SVN, and then perform a svn update to bring the host directory into sync with the SVN sources. The Web site directories (as opposed to files) are not maintained in synch with the SVN files automatically. They are manually updated from SVN by various people as they consider appropriate. This is usually not an issue, unless a group of files are being updated according to an ongoing group discussion.

httpd-dist
Like the httpd-site subtree, this one is used to maintain the files that comprise a website - in this case, http://downloads.apache.org/httpd/. Also like the previous subtree, the directory on the server is a checked-out working copy of this subtree. However, since this is a distribution directory, we only have the surrounding documentation and control files checked into this subtree -- the actual tarballs are simply copied to www.apache.org.

The SVN URL is https://svn.apache.org/repos/asf/httpd/httpd/dist.

Committers will generally deal with this subtree when "rolling" a release. This is a series of steps taken to create a complete new release of the Apache httpd software. Amongst other things, the key to this subtree is the tools/ directory, which contains the release.sh shell script. More information on the policies and procedures relating to rolling releases can be found on the Release Guidelines page.

Setting Up Remote SVN
A brief overview of getting started with SVN committer access can be found here. One key change to note is that SSH is not used anymore for committer access, due to the functional differences with SVN.
