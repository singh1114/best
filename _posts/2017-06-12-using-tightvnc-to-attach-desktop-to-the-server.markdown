---
author: ranvirsingh1114
comments: true
date: 2017-06-12 14:39:56+00:00
layout: post
link: https://ranvirsinghprojects.wordpress.com/2017/06/12/using-tightvnc-to-attach-desktop-to-the-server/
slug: using-tightvnc-to-attach-desktop-to-the-server
title: Using tightvnc to attach desktop to the server
wordpress_id: 705
categories:
- server
---

**INTRODUCTION:**

VNC is a virtual network computing which is used to add a desktop to the server and allows the users to use the server using mouse and keyboard. This allows the inexperienced user who wants to interact with the server to do this without using the commands.

**Difference between the server and the desktop OS:**

We know that we have to keep the server processor as free as possible. We do this by installing only the most important packages that can run the system efficiently. This allows us to skip the installation of the desktop system for the server. So, the server can only be used by some experienced user who knows few commands to use processes and adding various things to the server. Now as the server which does not have a desktop, it will be very difficult for a user who does not know some very basic commands.

For these users, VNC is introduced so that they can use the server easily. Now that we know why we need to have VNC, I will take this opportunity to explain installation procedures for the for VNC for Ubuntu 16.04.

In this tutorial, we are going to discuss the things for TightVNC which is an open source software that is available for both UNIX-based systems and Windows based systems. It is a kind of upgrade for VNC with lesser number of bugs. Here in this tutorial, we are going to discuss the installation of TightVNC for Ubuntu 16.04.

**INSTALLATION:**

First of all, let's test the procedure for the desktop. If you are doing the installation the server we need to install the basic desktop called xfce. For this, we need to apply this command.


<blockquote>`$ sudo apt-get install xfce4 xfce4-goodies tightvncserver`</blockquote>


Now after doing this installation, we need to configure the installation. For this apply this command,


<blockquote>`$ vncserver`</blockquote>


After applying this command, we have to give a password that will allow various users to connect to the server. The other option can allow the server to be view only. Using this option the server will become view only, that is we cannot change the things on the server but we can see what's happening on the server.

VNC launches a default server instance at 5901 which is called the display port when the VNC is first set up. This port is known as display port. We open the other ports by applying the following command.


<blockquote>`$ vncserver :2```</blockquote>


This commands opens up the port 5902 and so on.

Now as we want to change the way the server works, we need to stop the current instance. For that apply the following command.


<blockquote>`$ vncserver -kill :1`</blockquote>


Now apply the following command to edit the startup script for VNC.


<blockquote>`$ vim ~/.vnc/xstartup`</blockquote>


Add the following stuff to the file using usual [vim commands.](https://ranvirsinghprojects.wordpress.com/2016/06/09/vim-the-best-text-editor/)


<blockquote>`#!/bin/bash
xrdb $HOME/.Xresources
`

`startxfce4 &`</blockquote>


Run this command to give executable permissions to file created if you created the new file but if you have changed the earlier content then there is no need to apply this command.


<blockquote>`sudo chmod +x ~/.vnc/xstartup`</blockquote>


After that, you have to restart the system or restart the VNC service.

After restarting the system, start the VNC server using the following command.


<blockquote>`$ vncserver :1`</blockquote>


Now apply the following command to ssh to the server using the display port.


<blockquote>`$ ssh -L 5901:127.0.0.1:5901 -N -f -l username server_ip_address```</blockquote>


Where username is the user of the server and IP is the server IP address. Now apply the final command to see the desktop.


<blockquote>`$ vncviewer`</blockquote>


It will ask for the address. Give the following address.


<blockquote>`$ localhost :1`</blockquote>


You will see the desktop on the on your local screen.
