---
author: ranvirsingh1114
comments: true
date: 2016-07-30 20:50:03+00:00
layout: post
link: https://ranvirsinghprojects.wordpress.com/2016/07/31/adding-a-tuple-to-the-end-of-the-basic-tuple-in-python/
slug: adding-a-tuple-to-the-end-of-the-basic-tuple-in-python
title: Adding a tuple to the end of the basic tuple in python
wordpress_id: 239
categories:
- Django
- Six weeks training
---

Another problem was encountered while working on the python web framework, Django. But this time the problem was more of the language oriented rather than being framework oriented. As I am not a python programmer so I never knew these basic things. So, first of all I was getting an error, whose statement went like this :

First of all I will like to tell the things that I wanted to iterate over were stored in list and the list has many tuples inside it.



    
    <code>[('name1'), ('name2')]</code>


There was a large list of names. The only plus point in this journey was that I already had a tuple that was showing the required result. And the tuple which worked was looking like this..



    
    <code>(('abc1','xyz1'),('abc2', 'xyz2'))</code>


So, The first thing I did was that I converted the list into the tuple if 'l' is the name of the list.

**Convert a python list into tuple**

    
    <code>l=tuple(l)</code>


The final tuple will be stored in l. After working on this error I went forward to run the python server. The server showed an error. The error said..

_Need more than one value to unpack._

I went forward and again compared my tuple with the working tuple and after comparing I came to know that I must have a pair of two values in the single tuple so that they can the django can unpack them accordingly(I don't know the basic reason behind this, This can be because the takes this format). This [link](http://interactivepython.org/runestone/static/pip2/Tuples/TupleAssignmentwithunpacking.html) can help you to learn more in the right direction.

For this I went forward to create a loop which can add a new items in the end of the tuple. Now as the tuple in python is immutable so that when we add the data to tuple the data is added as a tuple. This is what I wanted but whenever I searched for something like this on the internet I got other ways of doing that and one of them said that you need to convert the tuple into a list and then add the data.

But the problem was solved by using this code in the for loop:

    
    <code>x = 0
    for q in name:
    	z=((q.id, q.Name),)+z
    	x = x+1</code>


This is how I solved the most persistent problem in the project. Please share your views about the post in the comments.
