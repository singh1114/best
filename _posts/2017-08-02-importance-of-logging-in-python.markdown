---
title: Importance of logging in python
date: 2017-08-02 23:08:37 Z
categories:
- GSoC-2017
author: ranvirsingh1114
comments: true
layout: post
link: https://ranvirsinghprojects.wordpress.com/2017/08/03/importance-of-logging-in-python/
wordpress_id: 849
---

Not in the mood of writing much today so will probably leave the link which I found useful and will definitely help us if we want to know more about logging.

[https://fangpenlin.com/posts/2012/08/26/good-logging-practice-in-python/](https://fangpenlin.com/posts/2012/08/26/good-logging-practice-in-python/)

There's only one thing that they have not explained properly and that is the use of ```__name__. Basically, this will tell the name of the file and improve the log message. This helps us to make more sense of the logging message and we can tell where the error occurred during the program execution.
