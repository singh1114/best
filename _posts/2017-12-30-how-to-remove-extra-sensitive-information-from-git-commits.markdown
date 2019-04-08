---
author: Ranvir Singh
comments: true
date: 2017-12-30 07:46:54.178447
layout: post
title: How to remove extra sensitive information from git commits
slug: how-to-remove-extra-sensitive-information-from-git-commits
categories:
- GitHub
- GitHub Pages
- Jekyll
- Remove commits
---
Many times we out of knowledge give extra sensitive information to files and directories and send them into Git. Git being the version control system saves everything into the system. So if you add a password to a file which you can't really change in the future, Git will store the password forever. This way the hackers can take down your system.&nbsp;

&nbsp;

Such thing happened to me when I launched [JekLog](http://jeklog.com), which is a blog creating platform using Jekyll and GitHub pages. I was using GitHub API for the web application. As the app was made by using Django( web development app of python), everything was needed&nbsp;to be saved in the settings.py file. I accidentally committed the files and pushed them to the GitHub pages. The files contained the password of my Gmail account. Thanks to google who saved my account from being hacked by sending a message to me about the suspense activity.&nbsp;

&nbsp;

After few days I found the damage done. I found the passwords written in my settings file. The damage was already done. I tried to find the solution. I found two solutions:

&nbsp;

*   BFG&nbsp;Repo-Cleaner
*   git filter-branch

&nbsp;

BFG is very popular and everyone is talking about it. They have a very good documentation but their installation guide is not that great for Ubuntu or any other Linux distros. I am going to discuss the other option which worked for me.

&nbsp;

`` $ cd YOUR_GIT_REPO ``

<code>$ git filter-branch --force --index-filter \<br/>
'git rm --cached --ignore-unmatch <em>PATH-TO-YOUR-FILE-WITH-SENSITIVE-DATA</em>' \<br/>
--prune-empty --tag-name-filter cat -- --all</code>

&nbsp;

You have to replace&nbsp;_PATH-TO-YOUR-FILE-WITH-SENSITIVE-DATA _with the file&nbsp;that contain the sensitive data. If you have more than one files insert them one by one in the same command. When done push the code to the repository with _force_ option to all the branches.&nbsp;

&nbsp;

`` $ git push origin --force --all ``

&nbsp;

You have to take care of all the forks too in the same way. From now onwards take a good care of such accidents by adding the special files to gitignore file. Otherwise, you can make use of ENV variables.

&nbsp;

Goodbye! Until the next time.