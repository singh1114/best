---
title: How to install django using virtual environment
date: 2016-07-18 10:27:00 Z
categories:
- python
- django
author: ranvirsingh1114
comments: true
link: https://ranvirsinghprojects.wordpress.com/2016/07/18/how-to-install-django-using-virtual-environment/
wordpress_id: 214
layout: post
---

A virtual environment is made when you want to run a different version of a single system. It is a clean way of handling different Python projects in your machine.

In this example, I am going to set up a virtualenv for installing Django 1.9. This is because the default version of python in the ubuntu system is 2.7(approx.) and the Django is in version 1.7.

Python is very important in the case of Ubuntu graphics. (If you want to test this try to remove Python from your system and get ready to waste 2-3 hours of your time trying to figure out what happened. **You might have to install Ubuntu again**).

Now it's time to start creating the virtual environment. So before installing virtualenv you need to have pip installed in your system. For that use this command.

```sudo apt-get install python-pip```

Now install virtualenv

```sudo pip install virtualenv```

and then

`sudo pip install virtualenv --upgrade` for the most recent version of the virtual environment.

Now make a directory where you want to run the virtual environment.

```mkdir django1_9_7```

```cd django1_9_7```

Now create a virtualenv inside this folder.

```virtualenv .```

Now apply this command every time you want to start the use the virtualenv

```source bin/activate```

Now you are in the virtual environment and you can see the various packages inside this env are going to stay in this env only. Use this command to find the packages in the env

```pip freeze```

Now use this command to install Django

```pip install django```

Now you can start a Django project inside this folder.

```django-admin startproject myprojectname .```

This environment will be as same as the way and the real installed software will work. Thanks for reading, do share it with your friends.
