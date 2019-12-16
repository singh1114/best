---
title: HTML presentation framework reveal.js and why I am a big fan?
date: 2016-04-07 09:51:00 Z
author: ranvirsingh1114
comments: true
link: https://ranvirsinghprojects.wordpress.com/2016/04/07/making-a-presentation-in-reveal-js/
wordpress_id: 77
image: https://i.imgur.com/G5fQRw4.jpg
layout: post
---

Reveal.js is an HTML presentation framework that can help you to create awesome presentations for your talk or simple knowledge transfer session in your class.

![Creating presentations using HTML in reveal.js](https://i.imgur.com/G5fQRw4.jpg "Creating presentations using HTML in reveal.js")

I have created a number of presentations using reveal.js.

Here are the links:

* [https://ranvir.xyz/presentations/project1.html#/](https://ranvir.xyz/presentations/project1.html#/)
* [https://ranvir.xyz/presentations/slide2.html#/](https://ranvir.xyz/presentations/slide2.html#/)
* [https://ranvir.xyz/presentations/mathjax.html#/](https://ranvir.xyz/presentations/mathjax.html#/)
* [https://ranvir.xyz/presentations/csi.html#/](https://ranvir.xyz/presentations/csi.html#/)

## Prologue (How I came to know about reveal.js)

So, during my time at college I had to deliver a presentation to a group of students and teachers from a special student cell regarding one of the emerging technologies of those times.

My mentor at that time suggested me to use reveal for creating the presentation. I was skeptical in the beginning but as soon as I got the grip of it, I loved it. 

I went home and thought that it would be a difficult task but in the end, I ended up doing it just in two hours.

## setting up reveal.js

All you need to run reveal powered presentation in your local system is to have javascript up and running and if you reading this post, you definitely have it running.

All you have to do is to go to reveal.js GitHub page and download the latest version of the code on the website.

[Here is the link for reveal.js GitHub repository.](https://github.com/hakimel/reveal.js/)

The downloaded file would be a zip file. If in windows, open the file simply by double-clicking it.

If in Linux use these commands in the terminal to open the file. First of all download the unzipper by using this command.

`sudo apt-get install unzip`

Then use this code to unzip the file by giving a name of the destination folder.

`unzip file.zip -d destination_folder`

Otherwise, if you prefer, you can `fork` the code from the https://revealjs.com/)

After unzip open the folder and you will find an `index.html` file inside.

Open this file in your text editor. Inside the body, tags delete every section.

Now create each section using beginning and ending section tag. Each section is equivalent to one slide.

Here is the reference of one equivalent slide.

<script src="https://gist.github.com/singh1114/47444f83e62a50160d78791720c461c6.js"></script>

You can do a whole lot of things using reveal.js presentation creator. You can create a style of your own if you want to.