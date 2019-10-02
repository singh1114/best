---
title: Making a presentation in reveal.js
date: 2016-04-07 09:51:25 Z
author: ranvirsingh1114
comments: true
layout: post
link: https://ranvirsinghprojects.wordpress.com/2016/04/07/making-a-presentation-in-reveal-js/
wordpress_id: 77
---

So, I was asked to make a presentation in reveal.js.

I went home and thought that it would be a difficult task but in the end I ended up doing it just in two hours.

You have to keep in mind that in this post I am not going to discuss about how to setup reveal.js and will not talk about the other features discussed in the documentation of the reveal.js.

So, first of all go reveal.js GitHub page and download the latest version of the code on the website.

[Here is the link for reveal.js GitHub repository.](https://github.com/hakimel/reveal.js/)

The downloaded file would be a zip file. If in windows, open the file simply by double clicking it.

If in Linux use these commands in the terminal to open the file. First of all download the unziper by using this command.


<blockquote>_`sudo apt-get install unzip`_</blockquote>


Then use this code to unzip the file by giving a name of the destination folder.


<blockquote>_`unzip file.zip -d destination_folder`_</blockquote>


After unzip open the folder and you will find a index.html file inside.

Open this file in your text editor. Inside the body tags delete every section it.



Now create each section using beginning and ending section tag. Each section is equivalent to one slide.

This is the way in which reveal.js presentation is created.

Regards,
Ranvir Singh  
