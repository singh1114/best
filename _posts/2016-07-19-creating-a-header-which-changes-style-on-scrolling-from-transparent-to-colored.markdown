---
author: ranvirsingh1114
comments: true
date: 2016-07-19 18:26:58+00:00
layout: post
link: https://ranvirsinghprojects.wordpress.com/2016/07/19/creating-a-header-which-changes-style-on-scrolling-from-transparent-to-colored/
slug: creating-a-header-which-changes-style-on-scrolling-from-transparent-to-colored
title: Creating a header which changes style on scrolling | From transparent to colored
wordpress_id: 234
categories:
- CSS
- Six weeks training
---

Hello everyone, I am back with one more exciting post. In this post we are going to discuss something great. This is something that I always wanted to learn but waiting for someone who can force me search through the Google and create the desired results.

I promised myself that I will surely make use of this concept in my next project. Finally I used it while creating the main page of the website of Duggal Building Materials using Django([github link to the code](https://github.com/singh1114/Djangosite)) and now I am showing off my latest acquired skill.

**Task :**

So the final result that we want is a header with navigation bar that changes style when we scroll down on the browser. Let's clarify the situation and talk about the final result first. Finally we will have a transparent header if the user is at the top and opaque as soon as the user starts scrolling down. Now we are taking this as an example but you can do whatever you want to do after this.

Also by the end I will provide a single code file you must keep the code in the separate files. For example CSS, JavaScript must be in different files.

**Used Technologies :**

HTML, CSS, JS, jquery, Bootstrap and some more.

That is it for the prerequisites of the task and now is the time to accomplish it.



 	
  1. First of all add the requirements in the head of the html.

 	
  2. Now let's make a navbar using bootstrap.

 	
  3. Give this nav a id of header. We will target this id.

 	
  4. Then add a div that will provide the required room to see the scrolling action.

 	
  5. Now add the  following script.



    
    <!DOCTYPE html>
    <html>
    <head>
     <title>Some Title</title>
     <!-- Code for number 1 start -->
     <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css">
     <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/js/bootstrap.min.js">
     <a href="https://ajax.googleapis.com/ajax/libs/jquery/1.12.4/jquery.min.js">https://ajax.googleapis.com/ajax/libs/jquery/1.12.4/jquery.min.js</a>
     <link href="https://fonts.googleapis.com/css?family=Ubuntu:400,700" rel="stylesheet">
     <!-- Code for number 1 ends -->
    </head>
    <body>
    










**Your Header**


<ul class="nav navbar-nav" id="nav-list" style="float:right; color: #EA4525;"> <li class="active"><a href="/">Home</a></li> <li><a href="#">Products</a></li> <li><a href="">Contact Us</a></li> <li><a href="">About Us</a></li> </ul> </div> </nav> <!-- Code for number 2 ends --> </div> <!-- Code for number 4 start : height of 2000px is given -->



//script starts for number 5 $(document).ready(function(){ var scroll_start = 0; var startchange = $('#header'); var offset = startchange.offset(); $(document).scroll(function() { scroll_start = $(this).scrollTop(); if(scroll_start > offset.top) { $('#header').css('background-color', 'rgba(34,34,34,0.9)'); } else { $('#header').css('background-color', 'transparent'); } }); }); </body> </html>







That's it for this post. If this doesn't work out feel free to post a comment.
