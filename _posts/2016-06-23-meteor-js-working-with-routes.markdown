---
author: ranvirsingh1114
comments: true
date: 2016-06-23 22:46:58+00:00
layout: post
link: https://ranvirsinghprojects.wordpress.com/2016/06/24/meteor-js-working-with-routes/
slug: meteor-js-working-with-routes
title: 'Meteor.js : Working with routes'
wordpress_id: 165
categories:
- Meteor.js
- Six weeks training
---

As we all know that meteor can only be used to create a single page web apps. Still there are many instances when one want to work with different URL's on a web applications.

This problem in Meteor is solved by using routes. Whenever a user does some event(mostly tries to click on a link) on the website then we can create a route to different templates and open them on the client side creating a great user experience.

Now there are a lot packages available in the meteor for handling these routes. The two of them which are most famous are :



	
  * Iron router

	
  * Flow router


Both of them are great but I am going to use Flow router for my further learning process.

Flow router is created by a team at kadira: flow router. We can add this router to our application by using this command while we are in the meteor app root directory.


<blockquote>$ meteor add kadira:flow-router</blockquote>


Now run your app using the basic meteor command to run the app


<blockquote>$ meteor</blockquote>


This will run the app on localhost:3000. Now in the browser you can go to different routes to check this small example about the routes.

As the routes are very basic to client we can put them in the client folder present in the application but it is recommended that we must put them in the /lib folder inside the root folder. So first of all create a folder named lib when inside root folder of the app.

Now create a document with the name of routes.js. We are going to put all our routes in there. Here I am going to discuss the very basic example so that we can see whats happening. We can further extend our work from there on.

In the file write this content.

    
    <code class="  language-javascript">
    FlowRouter<span class="token punctuation">.</span><span class="token function">route</span><span class="token punctuation">(</span> <span class="token string">'/home'</span><span class="token punctuation">,</span> <span class="token punctuation">{</span>
      action<span class="token punctuation">:</span> <span class="token keyword">function</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
        console<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span> <span class="token string">"Welcome to the homepage"</span> <span class="token punctuation">)</span><span class="token punctuation">;</span>
      <span class="token punctuation">}</span><span class="token punctuation">,</span>
      name<span class="token punctuation">:</span> <span class="token string">'Home'</span>
    <span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;
    </span></code>


This type of route is known as static route which is used to create route for a static address. For example if we want to create a page for home we can create by using this type of route. Now go to http://localhost:3000/home and opening the browser console we can see the comment : "welcome to the homepage" (without quotes).

There is more to routers which I will talk in the upcoming post.

If something not correct in the post please comment below. If still confused feel free to contact using the comments.
