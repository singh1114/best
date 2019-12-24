---
title: 'CGI : Make it work for public_html directory'
date: 2016-06-19 09:53:49 Z
categories:
- BaKaplan
- cgi
- Six weeks training
author: ranvirsingh1114
comments: true
layout: post
link: https://ranvirsinghprojects.wordpress.com/2016/06/19/cgi-make-it-work-for-public_html-directory/
wordpress_id: 136
---

Hello everyone,

In this post we will discuss the way in which we will tell the server that we will place our output files in a directory inside the home folder and that output files must run on the particular link.

So, let's start the process. First of all we need a directory named public_html within which there should be a folder named cgi-bin in the home directory. The command for this process is,


<blockquote>mkdir -p ~/public_html/cgi-bin/</blockquote>


-p flag is used to create the directory no matter what and ~ sign represents the home directory.

Now as the folders are created we need to put some dummy file inside them and check out the results in the browser to make sure that everything is working properly. Go to the file.


<blockquote>$ cd ~/public_html/cgi-bin/

$ vim test.cpp</blockquote>


Now add this content to the file. Read [this post](https://ranvirsinghprojects.wordpress.com/category/vim/) if you want to know more about vim.


<blockquote>#include <iostream>
using namespace std;

int main ()
{

cout << "Content-type:text/html\r\n\r\n";
cout << "<html>\n";
cout << "<head>\n";
cout << "<title>Lello World - First CGI Program</title>\n";
cout << "</head>\n";
cout << "<body>\n";
cout << "<h2>Lello World! This is my first CGI program</h2>\n";
cout << "</body>\n";
cout << "</html>\n";

return 0;
}</blockquote>


Save this file with the name test.cpp or with any other .cpp extension.

Now if you are following the BaKaPlan tutorial, you will be having G++ installed in your system but before compiling this file we need to complete some steps that are important to configure this public_html folder.


<blockquote>$ sudo a2enmod userdir</blockquote>


Which mean apache2 enable mod. If you want to look more into this matter you can open the manual by using this command.


<blockquote>$ man a2enmod</blockquote>


When a2enmod command is used two new files are added in the list in the directory modes-enabled. The opposite command is a2dismod which means apache2 disable mode. when using terminal type these commands.


<blockquote>$ cd /etc/apache2/mods-enabled

$ ls</blockquote>


You will see two files added to list at the end named userdir.conf and userdir.load. These files helps in the cofiguration of the public_html folder. Now you must restart apache2 by using this command.


<blockquote>$ sudo service apache2 restart</blockquote>


Now you need to give permissions to the public_html folder. Use this command to give read permissions to others.


<blockquote>$ chmod -R 755 ~/public_html
$ sudo a2enmod cgi

$ sudo a2enmod cgid

$ sudo service apache2 restart

$ cd ~/public_html/cgi-bin/

$ cd /etc/apache2
$ sudo service apache2 restart
$ sudo apt-get install libcgicc-dev
$ sudo vim httpd.conf</blockquote>


Add this content to this file.


<blockquote>ScriptAlias /cgi-bin/ /home/*/public_html/cgi-bin/
<Directory "/home/*/public_html/cgi-bin">
AllowOverride None
Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
SetHandler cgi-script
Order allow,deny
Allow from all
</Directory></blockquote>


Now restart apache again


<blockquote>$ sudo service apache2 restart</blockquote>


Now it's time to compile the program. If you don't give any output name than compiled data will be saved in a file named a.out but you can give a name using -o flag.


<blockquote>$ g++ test.cpp -o test.cgi</blockquote>


test.cgi is the name of output file.

Now in the browser type this link by replacing username with your username.

http://localhost/~USERNAME/cgi-bin/a.out

If the output file shows itself on the browser then it's working. If not then you might have done something wrong. Follow the procedure again and solve the problem.

Still facing problem please comment below.


