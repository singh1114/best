---
layout: post
title: How to remove extra sensitive information from git commits and history
date: 2017-12-30T07:46:54.178Z
description: >-
  How to remove extra sensitive information from your commit history all
  together by using git filter-branch command.
published: true
tags:
  - git
  - github
  - jekyll
categories:
  - git
  - github
  - jekyll
---
Many times unknowingly we forget to remove sensitive information to files and directories and send them into Git.

{% include linked_post.html url="basic-commands-in-github" %}

Git being the version control system saves everything into the system. So if you add a password to a file which you can't really change in the future, Git will store the password forever.

Even if you try to delete the password in the current `HEAD` the information will stay there forever. This way the hackers can take down your system.

Similar thing happened to me when I launched [JekLog](http://jeklog.com)( No longer available), which was a blog creating platform using Jekyll and GitHub pages.

I recommend using [Siteleaf](https://siteleaf.com) instead.

I was using GitHub API for the web application. As the app was made by using Django( web development app of python), everything was needed to be saved in the settings.py file.

I accidentally committed the files and pushed them to the GitHub pages. The files contained the password of my Gmail account.

Thanks to google who saved my account from being hacked by sending a email to me about the suspense activity.

After few days I found the damage done. I found the passwords written in my settings file. The damage was already done. I tried to find the solution. I found two solutions:


*   BFG Repo-Cleaner
*   git filter-branch

BFG is very popular and everyone is talking about it. They have a very good documentation but their installation guide is not that great for Ubuntu or any other Linux distros. I am going to discuss the other option which worked for me.

`$ cd YOUR_GIT_REPO_PATH`

```bash
$ git filter-branch --force --index-filter \
'git rm --cached --ignore-unmatch <em>PATH-TO-YOUR-FILE-WITH-SENSITIVE-DATA</em>' \
--prune-empty --tag-name-filter cat -- --all
```

You have to replace _PATH-TO-YOUR-FILE-WITH-SENSITIVE-DATA_ with the file that contain the sensitive data. If you have more than one files insert them one by one in the same command. When done push the code to the repository with _force_ option to all the branches.


`$ git push origin --force --all`

You have to take care of all the forks too in the same way. From now onwards take a good care of such accidents by adding the special files to gitignore file. Otherwise, you can make use of ENV variables.

Goodbye! Until the next time.
