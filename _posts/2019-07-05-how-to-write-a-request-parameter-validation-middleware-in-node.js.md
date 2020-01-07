---
layout: post
title: How to validate your request parameters easily | Using middleware in node.js
date: 2019-07-05T15:55:00.000Z
description: >-
  Validate your request parameters using a validator middleware that can be
  plugged into any Nodejs/ Express application.
published: true
image: 'https://i.imgur.com/4BWtPKb.png'
tags:
  - Technology
  - Nodejs
  - javascript
categories:
  - Nodejs
  - Technology
  - javascript
---
Some time ago, I was working on a big Node.js application. All over the API's, I could see same validation for the request parameters being repeated again. Every API was literally checking if certain parameter was being passed by the frontend.

I get it! You don't want to repeat that code again and again. Maybe you are sick of copying those little function calls all over your code with some change in the parameters. Every time you have to create a new route or new API endpoint you have to write the same code.

![Validate your request parameters using a middleware](https://i.imgur.com/4BWtPKb.png "Validate your request param using middleware in node.js")

For example:

```javascript
// Inside the route.
if (!request.phone_number) {
    throw new Error('Main request parameter not present.');
}
```

If you are starting out your app, this might look fine but as your app keeps getting bigger and bigger, you might want to write some specific code that can handle this for you.

If you want to wrap all your requests with some special data, this tutorial is for you.

This will also be helpful for your developers to know which parameters are required for the given route and which of them are optional. All you need to do is create a **middleware** which will keep account of all your parameters.

In terms of web development, we call them middleware... Just a fancy name( makes sense though).

> Middleware is a piece of code that is used to make changes to request or response data.

A good example for which a middleware can be used is logging. You can log your request parameters, headers, response data to wherever you want to log it.

We are going to talk about a specific type of middleware in this article, but you can extend it to anything you want to.

## A middleware that can validate the request parameters.

How would you feel when you don't have to worry about the incoming request parameters in the routes?

Pretty awesome, right!

You will never have to make any check related to the request parameters. All these checks will be transported to the middleware.

## What is a middleware?

A middleware is a simple part of the code that is used to manipulate requests or response data.

Let's start by writing a simple middleware.

<script src="https://gist.github.com/singh1114/766113f61c4f61b8357e4ff0223ec3c1.js"></script>

So this is the simple structure of middleware in Node.js. There are three types of checks that are going on in there.

## Required Parameter check

This check tries to find if the parameter being requested is required or not. We can specify this while specifying the schema of the route parameters. I will share this schema a little later in this tutorial. If the parameter is required for the route and is not present in the parameters of the route, it will simply raise 400.

This can also give a custom message specifying which param exactly is not present in the request parameters. This part is described `on line 21`.

## Type check

Javascript being less strict related to the type of the variables, we want to add a check which will try to check if the type specified in the schema of the route parameters is the same as the type received from the request parameters.

This part of the code is written `on line 6`.

## Other validation checks

There are multiple occasions when you want to add your own validations to request parameters. For example, you don't want the value to be equal to 0. You can simply create the function and pass it in the schema of the route parameters. These checks are written `on line 13`.

Here is the schema for route parameters.

<script src="https://gist.github.com/singh1114/e33ef5764df3476bf7a6c83cf3e9359d.js"></script>

This is how you will create a route in your Nodejs app.

The cool thing about this is you can at any time integrate your own checks into this.

## Using Joi as a alternative to adding request parameter validator 

I later found that you can use [Joi](https://github.com/hapijs/joi) for adding validations to parameters. This is a good option and you can use it if you want.

They provide a lot of validations out of the box which are easy to plug in.

## Writing tests for simple request parameter validation middleware

One of my colleagues asked me to write tests for this framework as this was going to be used at a lot of places and I agreed with him. But I was a little skeptical on how can we test this framework. After some Googling and StackOverflowing, I was able to test this framework. Here is the code for this.

<script src="https://gist.github.com/singh1114/61495aff847d0a527cb039aaf8ffa408.js"></script>

I hope you guys will like the idea behind the post. Please share it with your colleagues and let me know on social media platforms.

I am also open to other standards that are followed in the market. Please leave your ideas in the comments.
