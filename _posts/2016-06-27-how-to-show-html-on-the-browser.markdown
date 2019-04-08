---
author: ranvirsingh1114
comments: true
date: 2016-06-27 22:09:33+00:00
layout: post
link: https://ranvirsinghprojects.wordpress.com/2016/06/28/how-to-show-html-on-the-browser/
slug: how-to-show-html-on-the-browser
title: How to show html on the browser
wordpress_id: 211
categories:
- Six weeks training
---

Sometimes we want to share html code on the browser for example today I wanted to give a presentation. This presentation was made with the help of reveal.js. Now reveal.js uses html to make presentations. There was some html code that I wanted to show on the browser. I searched on the web and found pre and code tag along with blockquote to show html on browser but it wasn't working as it was taking some of the html tags in the code and executing them.

So I went forward to find the solution for this after some more searching I found another situation which worked great form me.

So today I am going to share this here. Whenever you have to write <, which is also opening tag for HTML write &lt; instead and whenever you have to write >, use &gt;

For example if you have to write <head>, you can write


<blockquote>&lt;head&gt;</blockquote>


Still confused. Post a comment and I would be delighted to help. Thanks.
