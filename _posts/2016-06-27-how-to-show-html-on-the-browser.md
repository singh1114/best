---
layout: post
title: How to show html on the browser
date: 2016-06-27T22:09:00.000Z
published: true
tags:
  - html
  - javascript
categories:
  - Six weeks training
  - html
  - javascript
---

Sometimes we want to share HTML code on the browser, for example, today I wanted to give a presentation. This presentation was made with the help of reveal.js. Now reveal.js uses HTML to make presentations. There was some HTML code that I wanted to show on the browser. I searched on the web and found pre and code tag along with blockquote to show HTML on browser but it wasn't working as it was taking some of the HTML tags in the code and executing them.

So I went forward to find the solution for this after some more searching I found another situation which worked great form me.

So today I am going to share this here. Whenever you have to write `<`, which is also opening tag for HTML write `&lt;` instead and whenever you have to write `>`, use `&gt;`

For example, if you have to write `<head>`, you can write

`&lt;head&gt;`

Still confused. Post a comment and I would be delighted to help. Thanks.
