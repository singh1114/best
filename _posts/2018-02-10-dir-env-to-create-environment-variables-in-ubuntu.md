---
layout: post
title: How to use direnv to create environment variables in ubuntu or MAC
date: 2018-02-10T18:43:00.000Z
description: >-
  Using direnv to easily handle environment variables in your machine(Ubuntu/
  Mac). direnv apply your env variables whenever you enter the working
  directory.
published: true
image: 'https://i.imgur.com/Bo6A3zh.png'
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
redirect_from: []
---
{% include lazyload.html image_src="https://i.imgur.com/Bo6A3zh.png" image_alt="Handle environment variables like a pro" image_title="Handle environment variables like a pro" %}

## Introduction: Problem with Environment variables

Environment variables are very important for setting up important variables that you don't want to share in code.

In my project, I have to set up some important variable that I require all over my project for the development. For example database names, email passwords, private keys and all other such things.

But the problem with the environment variables is that you need to set them again and again. Everytime you come back to your shell, you have to export them again.

First of all, Let's discuss the way in which we can set environment variables without using direnv. The easiest way of creating these variables is as follows:

## Setting environment variables without direnv

```bash
$ export DB_USER=root
$ export DB_PASSWORD=ranvir
```

And correspondingly you can call these variables in the python file as follows:

{% include lazyload.html image_src="https://www.python.org/static/community_logos/python-logo-master-v3-TM.png" image_alt="Python Logo" image_title="Python Logo" %}

```python
import os
DB_USER = os.environ['DB_USER']
DB_PASSWORD = os.environ['DB_PASSWORD']
```

or in JavaScript.

```javascript
process.env.DB_USER
process.env.DB_PASSWORD
```

This way you can save yourself from sending very important secrets into your repository like I did some time ago and had gone through a very long process for deleting that code from GitHub.

In the meantime someone used the password and logged into my email account. Read the post about how I was able to [delete the password from GitHub code without deleting the repository](https://ranvir.xyz/blog/how-to-remove-extra-sensitive-information-from-git-commits/).

This is good solution, Right? There is no doubt that once you start using it, you will fall in love with such technology.

But in few days you will want to get out of typing in all the environment variables again and again after a shutdown or shifting of the bash shell. The solution of this problem is direnv.

## Install direnv in Ubuntu or MAC

[Direnv](https://github.com/direnv/direnv) is an open-source project used for proper setting of environment variables.

The idea behind this is that you set up all your variables in a single file called `.envrc` and the environment will be created as soon as you enter the directory in which `.envrc` file is present.

For installing `direnv` in ubuntu apply the following command:

```bash
$ sudo apt-get install direnv
```

or in MAC, use

```bash
brew install direnv
```

## Adding startup script in bashrc/ zshrc

After this, you have to add the following line at the end of the `~/.bashrc` file:

```bash
eval "$(direnv hook bash)"
```

Now if you are using `zsh` [as I do](https://ranvir.xyz/blog/set-up-new-machines-for-development/), you will have to add the following to `~/.zshrc` file.

```bash
eval "$(direnv hook zsh)"
```

What this line does is that, whenever you do anything on your shell, like opening new terminal window or moving to new directories. This will add a hook to load environment variables if `.envrc` is present.

Now go to a directory where you want to launch the environment variables.

As long as you stay in that directory the value of environment variables will not change. 

Use the following commands to create a file

```bash
$ touch .envrc 
```

Open the file in your favourite text editor and add the following content. I myself prefer Vim. Read more about Vim on following post.

{% include linked_post.html url="vim-the-best-text-editor" %}

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

{% include lazyload.html image_src="https://i.imgur.com/1kiOkyb.png" image_alt="Direnv loading and unloading" image_title="Direnv loading and unloading" %}

As long as you stay somewhere inside the directory, environment variable will always be available.

This now starts working as the virtual environment. Read more about virtual environments on this post.

{% include linked_post.html url="how-to-install-django-using-virtual-environment" %}

Do share your views about the post.
