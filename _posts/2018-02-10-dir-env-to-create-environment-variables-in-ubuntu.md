---
layout: post
title: How to use direnv to create environment variables in ubuntu
date: 2018-02-10T18:43:00.000Z
description: >-
  Using direnv to easily handle environment variables in your machine(Ubuntu/
  Mac). direnv apply your env variables whenever you enter the working
  directory.
published: true
tags:
  - python
  - direnv
  - environmentvariables
  - productivity
categories:
  - python
  - direnv
  - environmentvariables
  - productivity
canonical_url: ''
---

![python logo](https://www.python.org/static/community_logos/python-logo-master-v3-TM.png "Python Logo")

Environment variables are very important for setting up important variables that you don't want to share in code. In my project, I have to set up some important variable that I require all over my project for the development. For example database names, email passwords, private keys and all other such things. But the problem with the environment variables is that you need to set them again and again. Everytime you come back to your shell, you have to create them again.

First of all, Let's discuss the way in which we can set enviorment variables without using direnv. The easiest way of creating these variables is as follows:

```bash
$ export DB_USER=root
$ export DB_PASSWORD=ranvir
```

And correspodingly you can call these variables in the python file as follows:

```python
import os
DB_USER = os.environ['DB_USER']
DB_PASSWORD = os.environ['DB_PASSWORD']
```

This way you can save yourself from sending very important code into you repository like I did some time ago and had go through a very long process for deleting that code from GitHub. In the mean time someone used the password and logged into my email account. [Read the post about how I was able to delete the password from my account without deleting the repository](http://singh1114.github.io/blog/how-to-remove-extra-sensitive-information-from-git-commits/).

This is good solution, Right? There is no doubt that once you start using it, you will fall in love with such technology. But in few days you will want to get out of typing in all the environment variables again and again after a shutdown or shifting of the bash shell. The solution of this problem is direnv.

[Direnv](https://github.com/direnv/direnv) is an open-source project used for proper setting of environment variables. The idea behind this is that you set up all your variables in a single file called **.envrc** and the environment will be created as soon as you enter the directory in which .envrc file is present.

For installing **direnv** in ubuntu apply the following command:

```bash
$ sudo apt-get install direnv
```

After this, you have to add the following line at the end of the `~/.bashrc` file:

```bash
eval "$(direnv hook bash)"
```

Now go to a directory where you want to launch the environment variables. As long as you stay in that directory the value of environment variables will not change. 

Use the following commands to create a file

```bash
$ touch .envrc 
```

Open the file in your favourite text editor and add the following content. I myself prefer [vim](http://singh1114.github.io/blog/vim-the-best-text-editor/)

```bash
export DB_NAME=abc                                                          
export DB_USER=root
```

Save and close the file. The following error will be reported when you close the file.

```bash
direnv: error .envrc is blocked. Run `direnv allow` to approve its content
```

Do as the error say. Apply the following command and start using the environment variables:

```bash
$ direnv allow
```

Applying the command will give the following result:

```bash
direnv: loading .envrc
direnv: export +DB_NAME
...
```

When you leave the directory the following result will be shown:

```bash
direnv: unloading
```

This now starts working as the virtual environment. [Read more about virtual environments](http://singh1114.github.io/how-to-install-django-using-virtual-environment/)

Do share your views about the post.
