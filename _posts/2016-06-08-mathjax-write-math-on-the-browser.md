---
title: 'MathJax : Write math on the browser'
date: 2016-06-08 08:52:00 Z
author: ranvirsingh1114
comments: true
link: https://ranvirsinghprojects.wordpress.com/2016/06/08/mathjax-write-math-on-the-browser/
wordpress_id: 121
layout: post
---

First of all I would like to link to the presentation which you can check. This presentation will let you more about the MathJax.

[http://singh1114.github.io/presentations/mathjax.html](http://singh1114.github.io/presentations/mathjax.html#/)/

MathJax is a tool which is used to lay out the math on the browser in a better way. Tex and Latex has been used since a while now to write big mathematical formulas in the form of a pdf. MathJax make use of these two ways to write math on the browser.

MathJax is a JavaScript library which can be used in collaboration with Tex, Latex, MathML and AsciiMath. These three are used to write mathematical formulas at various points.

Prior from MathJax images were used to put a mathematical formulas on the browser which was quite a big deal to lay them out properly on the browser. Also these images were headache for the visually impaired people as screen reader were not able to guess what was written on the image. To solve all these problems MathJax was introduced.

There are two ways to implement Mathjax.
 	
  1. Through CDN (content delivery network)	
  2. By downloading the files

Now let us discuss about the CDN implementation. This implementation is discussed properly in the documentation on the MathJax official website. Here is the link for it.

[http://docs.mathjax.org/en/latest/start.html](http://docs.mathjax.org/en/latest/start.html)

In the head section of your website write these lines of code.


<blockquote><head>

MathJax.Hub.Config({tex2jax: {inlineMath: [['$','$'], ['\\(','\\)']]}});

[https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS_CHTML](https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS_CHTML)
</head></blockquote>


Now you can use Tex, Latex, MathML or Asciimath code anywhere on the page and that will be implemented as a mathematical formula.

If you wish see an example here is the link.

http://singh1114.github.io/mathjaxprogram.html

Another way of doing it is by cloning the github repository. Clone the github repository and you will find the a folder named test. In there you will find a file named example.html. Run this file and run various examples. Create any files in this folder and add script files as in the examples add any Tex, Latex or MathML content to show them on the browser.
