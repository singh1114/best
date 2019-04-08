---
author: ranvirsingh1114
comments: true
date: 2016-05-30 09:58:17+00:00
layout: post
link: https://ranvirsinghprojects.wordpress.com/2016/05/30/new-task-designaids/
slug: new-task-designaids
title: 'New Task : DesignAids'
wordpress_id: 112
categories:
- DesignAids
---

I was given a new task to run and use DesignAids on my system.

This links to the GitHub repository of DesignAids.

https://github.com/GreatDevelopers/DesignAids

According to the README.md file I have to install some preliminary softwares before trying my hand with the DesignAids. These softwares include LaTex, SageMath and biber.

So, I am going to install the first software i.e. LaTex. The internet connection is weak due to the weather problem so I have to wait for long time before this task is complete.

[Installing LaTex.](https://ranvirsinghprojects.wordpress.com/2016/05/31/installing-latex-to-your-system/)
[Installing SageMath and Biber.](https://ranvirsinghprojects.wordpress.com/2016/05/31/installing-sagemath-and-biber-into-the-system/)

After doing all these things I had to clone this DesignAids repository to my local computer. I created a directory in documents folder and clonned the repository inside it using the command.

    
    git clone https://github.com/GreatDevelopers/DesignAids


After cloning I changed directory inside this folder and then used these command to run main.tex file

    
    1)pdflatex main.tex
    2)biber main
    3)sage main.sagetex.sage
    4)pdflatex main.tex




After this I used make command to run this file.

    
    make
    make view
    make clean


![Screenshot from 2016-05-31 02-29-42](https://ranvirsinghprojects.files.wordpress.com/2016/05/screenshot-from-2016-05-31-02-29-42.png?w=300)
