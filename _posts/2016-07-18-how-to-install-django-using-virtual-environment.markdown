---
title: How to install django using virtual environment
date: 2016-07-18 10:27:27 Z
categories:
- Six weeks training
author: ranvirsingh1114
comments: true
layout: post
link: https://ranvirsinghprojects.wordpress.com/2016/07/18/how-to-install-django-using-virtual-environment/
wordpress_id: 214
---

Virtual environment is made when you want to run different version on single system. In this example I am going to setup a virtualenv for installing django 1.9. This is because the default version of python in the ubuntu system is 2.7(approx.) and the django is in the version 1.7. And the python is very important in the case of Ubuntu graphics. (If you want to test this try to remove python from your system and get ready to waste 2-3 hours of your time trying to figure out what happened. You might have to install Ubuntu again).

Now it's time to start creating the virtual environment. So the before installing virtualenv you need to have pip installed in your system. For that use this command.

```sudo apt-get install python-pip```

Now install virtualenv

```sudo pip install virtualenv```

and then

```sudo pip install virtualenv --upgrade``` for the most recent version.

Now make a directory where you want to run the virtualenv.

```mkdir django1_9_7```

```cd django1_9_7```

Now create a virtualenv inside this folder.

```virtualenv .```

Now apply this command everytime you want to start the use the virtualenv

```source bin/activate```

Now you are in the virtualenv and you can see the various packages inside this env are going to stay in this env only. Use this command to find the packages in the env

```pip freeze```

Now use this command to install django

```pip install django```

Now you can start a django project inside this folder.

```django-admin startproject myprojectname.```

This env will as same as the way as the real installed softwares will work..
