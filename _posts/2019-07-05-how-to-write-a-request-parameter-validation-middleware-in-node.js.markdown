---
author: Ranvir Singh
comments: true
date: 2019-07-05 15:55:15.964509
layout: post
title: How to write a request parameter validation middleware in node.js
slug: how-to-write-a-request-parameter-validation-middleware-in-node.js
---
I get it! You don't want to repeat that code again and again. Maybe you are sick of writing it again and again. Every time you have to create a new route or new API endpoint you have to write the same code.

&nbsp;

In terms of web development, we call them middleware... Just a fancy name( makes sense though). Middleware is something which is used to make changes to request or response data.

&nbsp;

I have seen people doing a lot of things in the middlewares.&nbsp;The best thing that one can do in the middlewares is logging. You can log your request parameters, headers, response data to wherever you want to log it.

&nbsp;

You can extend this article with your programming skills to create anything you want, but in this one, we are going to discuss a specific type of middleware.&nbsp;

&nbsp;

A middleware that can validate the request parameters.

&nbsp;

How would you feel when you don't have to worry about the incoming request parameters in the routes?

&nbsp;

Pretty awesome, right!

&nbsp;

You will never have to make any check related to the request parameters. All these checks will be transported to the middleware.

&nbsp;

Let's start by writing a simple middleware.

&nbsp;

<script src="https://gist.github.com/singh1114/766113f61c4f61b8357e4ff0223ec3c1.js"></script>

&nbsp;
&nbsp;