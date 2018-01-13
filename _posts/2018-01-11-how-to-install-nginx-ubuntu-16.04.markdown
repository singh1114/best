---
author: Ranvir Singh
comments: true
date: 2018-01-11 07:46:54.178447
layout: post
title: How to install nginx in Ubuntu 16.04
slug: how-to-remove-extra-sensitive-information-from-git-commits
categories:
- nginx
- apache2
- installation
- ubuntu
---
Today we are going to talk about the installation process of nginx which is used as a server and is known for the providing better services in the production environment. I have been using apache2 from a long time. Recently, I got the opportunity to use nginx for one of my recent project. Before starting I want to say that I was already using apache2 for any service I was providing and using on my local services. If you already have apache2 installed and you want to run nginx then you have to stop the apache2 two service otherwise you will receive the error like: 

```
Errors were encountered while processing:
 nginx-core
 nginx
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

To stop the apache2 service, use the following command.

```
sudo service apache2 stop
```

For installing nginx in Ubuntu 16.04, use the following command.

```
sudo apt-get install nginx
```

Check the status of the nginx server

```
sudo systemctl status nginx
```

If you get the green light or something like: `active` you are good to go. Do share your views using the comments below.