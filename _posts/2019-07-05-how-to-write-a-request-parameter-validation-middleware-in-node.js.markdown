---
title: How to write a request parameter validation middleware in node.js
date: 2019-07-05 15:55:15.964000000 Z
author: Ranvir Singh
comments: true
layout: post
---

I get it! You don't want to repeat that code again and again. Maybe you are sick of copying those&nbsp;little function calls all over your code with some change in the parameters. Every time you have to create a new route or new API endpoint you have to write the same code.

&nbsp;

If you want to wrap all your requests with some special data this tutorial is for you.

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

So this is the simple structure of middleware in Node.js. There are three types of checks that are going on in there.

&nbsp;

__Required Parameter check__

This check tries to find if the parameter being requested is required or not. We can specify this while specifying the schema of the route parameters. I will share this schema a little later in this tutorial. If the parameter is required for the route and is not present in the parameters of the route, it will simply raise 400.

&nbsp;

This can also give custom message specifying which param exactly is not present in the request parameters. This part is described on line 21.&nbsp;

&nbsp;

__Type check__

Javascript being less strict related to the type of the variables, we want to add a check which will try to check if the type specified in the schema of the route parameters is same as the type received from the request parameters.

&nbsp;

This part of the code is written on line 6.

&nbsp;

__Other validation checks__

There are multiple occasions when you want to add your own validations to request parameters. For example, you don't want the value to be equal to 0. You can simply create the function and pass it in the schema of the route parameters. These checks are written on the line 13.

&nbsp;

Here is the schema for route parameters.

<script src="https://gist.github.com/singh1114/e33ef5764df3476bf7a6c83cf3e9359d.js"></script>

&nbsp;

This seems to be self-explanatory. If you still have questions, feel free to post them in the comment section.

&nbsp;

The cool thing about this is you can at any time integrate your own checks into this.

&nbsp;

__Edit 1:&nbsp;__

I later found that you can use Joi for adding validations to parameters. This is a good option and you can use it if you want.

&nbsp;

__Edit 2:__

One of my colleagues asked me to write tests for this framework as this was going to be used at a lot of places and I agreed with him. But I was a little skeptical on how can we test this framework. After some Googling and StackOverflowing, I was able to test this framework. Here is the code for this.

&nbsp;

<script src="https://gist.github.com/singh1114/61495aff847d0a527cb039aaf8ffa408.js"></script>

&nbsp;

Hope&nbsp;you guys will like the idea behind the post. Please share it with your colleagues and let me know on social media platforms.

&nbsp;

I am also open to other standards&nbsp;that are followed in the market.

&nbsp;

Till the next time.