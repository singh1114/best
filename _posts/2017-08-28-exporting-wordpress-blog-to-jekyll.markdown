---
author: Ranvir Singh
comments: true
date: 2017-08-02 23:08:37+00:00
layout: post
slug: export_wordpress_blog_to_jekyll
title: Export Wordpress Blog to Jekyll
categories:
- GitHub
- Jekyll
---

This is the first time I am posting myself on this blog. Earlier posts are just been exported from wordpress so you will find some bad in them. But I am sure from now ownwards, this is my the new home for all my posts. I don't know how to tell my readers that I have posted something new on my blog but I will figure it out later.

So, today in this post I will discussing the way in which you can export all the posts from the wordpress blog and use it for your Jekyll blog. But, first let's discuss about the WHY. Why would someone try to quit WordPress and use the awesome service of Jekyll along with the GitHub pages to publish his/her blogs. I have been using the services of WordPress from a long time and I feel like I am the write person to answer this question.

While using the free services of WordPress, I found that it doesn't provide you the freedom to really do anything great with your content. Also being the technical person I have to insert code at various location in my code. Wordpress might be good for the photo blogs and other such blogs but it is not good for the technical blogs.

Coming back to the topic

**Exporting WordPress blog**

There are many ways to export a wordpress.com blog, but the one that I found useful and easy was making use of [exitwp](https://github.com/thomasf/exitwp). The tool is easy to use and everything is described in the documentation itself. Few easy steps and you are ready to go. Simply download the `xml` file by using export tool of WordPress and place the xml file in `wordpress-xml` directory in the `exitwp` code that you just cloned. Now simply run the script and it will produce all the posts for you.

```
$ python exitwp.py
```

Now go on place all the posts generated into the `_posts` directory of your `Jekyll` blog. Commit the changes and push the code. You will find the changes reflected on the blog in few seconds.
