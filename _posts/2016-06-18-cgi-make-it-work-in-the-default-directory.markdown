---
author: ranvirsingh1114
comments: true
date: 2016-06-18 20:30:18+00:00
layout: post
link: https://ranvirsinghprojects.wordpress.com/2016/06/19/cgi-make-it-work-in-the-default-directory/
slug: cgi-make-it-work-in-the-default-directory
title: 'CGI : Make it work in the default directory'
wordpress_id: 131
categories:
- BaKaplan
- cgi
- Six weeks training
---

Hello everyone,

If we want to make CGI work, we first must know that why is it used.

To know about the prerequisites read[ this post. ](http://wp.me/p7kUg1-26)

CGI stands for Common Gateway Interface. CGI help you to compiled program output through the browser window. If we don't have any tool to show the output of the program on the browser then output file(obj file in the case of C program) will be downloaded. Also CGI is not only used in the case of C or C++ but it can be for many other languages.

Also before going further into the topic I want to discuss some more about how the apache2 server works. This server recognizes a directory as its default working directory and shows out any html page in this directory which have read permissions to others. As when working with the browser we are working as others. This command can be used to open up the folder that folder of the server. Just add a file


<blockquote>cd /var/www/apache2/html/</blockquote>


Now if we want to show the output of the file on the browser through localhost then we must put the output file here or we must tell that the files in the next other directory must be treated as such to show the result in the browser.

So the procedure for this is explained on two of my friend's blogs. Please check these both procedures as both of them show different ways in which CGI can be configured in the default directory.

[https://amisha2016.wordpress.com/2016/02/18/task-2/](https://amisha2016.wordpress.com/2016/02/18/task-2/)

[https://iamjagjeetubhi.wordpress.com/2016/06/03/cgi-in-c/](https://iamjagjeetubhi.wordpress.com/2016/06/03/cgi-in-c/)

There might be some mistakes in both of the posts. If you find any, then you must comment it in the there respected blogs.

Still need help please comment below.
