---
title: Export Wordpress Blog to Jekyll
date: 2017-08-28 23:08:00 Z
categories:
- GitHub
- Jekyll
- Blog
- Technology
tags:
- GitHub
- Jekyll
- Blog
- Technology
author: Ranvir Singh
comments: true
layout: post
---

This is the first time I am posting on this blog. All the posts before this date have been exported from WordPress so you will find some mistakes in them. But I am sure from now onward, this is the new home for all my blog posts. I am very new to the Jekyll but I will like to learn it as fast as possible.

So, today in this post I will be discussing the way in which you can export all the posts from the WordPress blog and use it for your Jekyll blog. But, first let's discuss about the big question i.e. the WHY. Why would someone try to quit WordPress and use the services of Jekyll along with the GitHub pages to publish his/her blogs? I have been using the services of WordPress from a long time and I feel like I am the right person to answer this question.

While using the free services of WordPress, I found that it doesn't provide you the freedom to really do anything great with your content. Also being the technical person I have to insert code at various location in my code. WordPress might be good for the photo blogs and other such non-technical blogs but it is not good for the technical people. There is a reason for this too. Most of the techies out there don't really like to use the mouse or touchpad. They always want to avoid the usage of mouse or touchpad. They always want to keep their fingers on the keyboard. And when we compare WordPress and Jekyll on these fronts, we will find that WordPress lags behind Jekyll.

Coming back to the topic which is,

**Exporting WordPress blog**

There are many ways to export a WordPress.com blog, but the one that I found useful and easy was making use of [exitwp](https://github.com/thomasf/exitwp). The tool is easy to use and everything is described in the documentation itself. Few easy steps and you are ready to go. Simply download the `xml` file by using export tool of WordPress and place the XML file in `wordpress-xml` directory in the `exitwp` code that you just cloned. Now simply run the script and it will produce all the posts for you.

To run the script use the following command.

```
$ python exitwp.py
```

Now go on place all the posts generated into the `_posts` directory of your `Jekyll` blog. Commit the changes and push the code. You will find the changes reflected on the blog in few seconds.

Post all the questions using the comments section.
