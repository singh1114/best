---
author: ranvirsingh1114
comments: true
date: 2016-08-03 17:45:34+00:00
layout: post
link: https://ranvirsinghprojects.wordpress.com/2016/08/03/how-to-create-a-session-variable-in-django/
slug: how-to-create-a-session-variable-in-django
title: How to create a session variable in Django
wordpress_id: 246
categories:
- Django
- Six weeks training
---

Long time ago browser developers recognized that we need to store the data produced during a user session so that we can refer to that data in the future. The user actions can lead to some calculations and after doing this cumbersome calculations we don't want to do the calculations again and again.

There is one more restriction in the web development i.e. whenever the URL changes all the variables in that particular URL are lost. So this future required data must be saved, and many times the database is not the right solution for this type of restriction because of the obvious reasons( one of them being speed).

This restriction was resolved by the use of cookies. Now we have been hearing this word from long time. We all know that the browser have cookies which is used to save the recently and most viewed web pages. As these cookies are storage spaces we can store some variables in the cookies. These variables are known as session variables.

Now it is perfectly easy to attain the required result in JavaScript. I will write a post on that which will help you to create a simple session variable in JavaScript but today we are going to talk about python web development framework i.e. Django.

Before starting with the coding part I want to discuss the circumstances that forced me to use this out of the box solution.

The reason was pretty obvious and self explanatory. I was having to different web pages, and I wanted to show same variable on both the pages. On the first page the variable was calculated from two or three variables which were posted to this page using a FORM. Now this page can easily show the variable on this particular page, but showing this variable on the next page where the user reached by clicking a button was a difficult task. Also I have no model(database) to store this variable. So I decided to use the session variables.

I also want to tell that this might not be the only solution to this kind of problem. If you have a more efficient solution then you are welcome to post a comment.

Now it's time to dive right into the coding part:

    
    <code>var1 = "ranvirsingh"
    request.session['name'] = var1</code>


This code stores the variable 'name' with a value 'ranvirsingh'. Now whenever you want to show this code on the browser you need to 'get' this variable and then you can show on that page.

    
    <code>var1 = request.session.get('name')
    </code>


Now you can use the name 'var1' and show it wherever you want.

That's it for this post. If you have some questions then feel free to comment below.
