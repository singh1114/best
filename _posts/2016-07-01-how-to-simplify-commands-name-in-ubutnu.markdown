---
author: ranvirsingh1114
comments: true
date: 2016-07-01 19:54:07+00:00
layout: post
link: https://ranvirsinghprojects.wordpress.com/2016/07/02/how-to-simplify-commands-name-in-ubutnu/
slug: how-to-simplify-commands-name-in-ubutnu
title: How to simplify command's name in Ubutnu
wordpress_id: 221
categories:
- Six weeks training
---

I love the amount of freedom given to you as a user when you work on a system with Ubuntu installed on it. So, I was not having sudo powers for the installing meteor on the server, So I asked one of the server admin([Mandeep](https://mandeep7.wordpress.com/)) to do it for me. He told me that I don't need to be signed as a root admin. I was not sure about it as their was a error when I was running the command to install meteor.

So he showed me the way to use the meteor commands on the server. A hidden folder was attached to my home directory with this name .meteor. He told me that if I go inside this folder then I can use the meteor commands by the name ./meteor. For example when I have to type meteor create appname, I will use ./meteor create appname. This wasn't looking great so he told me that I can change it accordingly. He left this job to me.

So I was thinking that how can I solve this problem. First I tried to make a variable of ./meteor command by using this. By using this command.


<blockquote>meteor='./meteor'</blockquote>


Now I was using $meteor command in place of .meteor. This was something better then ./meteor. But I wanted to make it work as required so after searching a bit I came to know about aliases in the Ubuntu.

So, when in home directory use this command.


<blockquote>vim .bash_aliases</blockquote>


Else everything is explained in this post. Just one thing, that sometimes you need to close the terminal to make this thing work.

[http://www.howtogeek.com/73768/how-to-use-aliases-to-customize-ubuntu-commands/](http://www.howtogeek.com/73768/how-to-use-aliases-to-customize-ubuntu-commands/)

I used this and everything was working on the server. But I wanted to implement on my local so I used the same procedure on the local. But somehow It was not working I tried to quit the terminal and tried to turn it on but it was not working.

I searched some more and found the solution. So you have to add some data into the file .bashrc(rc stands for "run commands") which is in the home directory. So add this data to the end of this file.


<blockquote>if [ -f  $ HOME/.bash_aliases  ]
then
.  $HOME/.bash_aliases
fi</blockquote>


Now try to restart the terminal and this will work for you.

Still not getting put your questions in the comment section. Thanks :)
