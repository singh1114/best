---
title: 'BakaPlan : Baithne ka plan (Generate Seating Plan)'
date: 2016-06-22 21:39:17 Z
categories:
- BaKaplan
- Six weeks training
author: ranvirsingh1114
comments: true
layout: post
link: https://ranvirsinghprojects.wordpress.com/2016/06/23/bakaplan-baithne-ka-plan-generate-seating-plan/
wordpress_id: 130
---

Hello everyone,

Sir said this before giving the task to me.


<blockquote>Reading other's code is very important task that every CS engineer must know. And BaKaPlan is the software that is written by following all the coding standards. You must always follow these standards.</blockquote>


In this post I am going to discuss about the BaKaPlan. This task was assigned to me by [sir](http://hsrai.wordpress.com/). He wanted me to read about this software and make it work on my system. He also wanted me to read about the code and make a list in the way it works.

In this post I will write the point on which I have reached in the process.

The specific and the tasks which I have completed during the process that I really want to discuss are :-



 	
  * Running CGI on the localhost server.

 	
  * Running CGI in the public_html folder.

 	
  * Configuring exim4 mail server


During this problem I faced a lot of problems and learned a lot of things. I solved these problems by the help of seniors and other trainees in the group. Some of which I would like to discuss here :-

 	
  * what to do when your GUI doesn't work.

 	
  * The things that didn't worked for me while


So, let's start with the BaKaPlan....

This is the software that can be used to make the seating plans for an examination. This software also provides some of the other options that we can work with to come up with a better solutions for all the seating problem. We will talk more about the things that it provide but first of all we will discuss the things that are required to make this software work on our system(your system : If you are doing it with this post).

**Requirement #1 : Apache server**

Most of the people may already have this thing in the local system but if you haven't got it use this command:


<blockquote>sudo apt-get install apache2</blockquote>


**Requirement #2 : GNU G++ compiler**


<blockquote>sudo apt-get install g++</blockquote>


**Requirement #2 : CGICC library**


<blockquote>sudo apt-get install libcgicc-dev</blockquote>


It's time to create a branch of this post. This branch will tell help you to make your CGI work at the default directory in the system. For Ubuntu this place is /usr/lib/cgi-bin/

[Read the post by clicking here.](http://wp.me/p7kUg1-27)

Now it's time to make it work on the place where it is required for this software i.e. In the home inside the public_html folder.

To know more about this process [read this post.](http://wp.me/p7kUg1-2c)

The next process is pretty straight forward and can be done by following this link.

[https://github.com/GreatDevelopers/bakaplan/](https://github.com/GreatDevelopers/bakaplan/)

After this we have go to the installation procedure. The installation process is done by cloning the bakaplan repository and configuring the database. For this you can go to the link below.

[https://github.com/GreatDevelopers/bakaplan/blob/master/INSTALLATION.txt](https://github.com/GreatDevelopers/bakaplan/blob/master/INSTALLATION.txt)

Now on going to the link the bakaplan page shows up but I am unable to log In. Every time I tried to log In to the system using the data given in the files it says that you need to login to the website and when I register to the website it says check your e-mail. When I check the e-mail it doesn't show anything about the bakaplan. I have checked everywhere, even in the spam folder.

I put the mail regarding this issue into the mailing list but no reply has came so far.

There were some other things tried by me before putting the question in the mailing list. For that I will come up with next post. So, read the next post in this category.

If you have any doubt in this section please comment below.
