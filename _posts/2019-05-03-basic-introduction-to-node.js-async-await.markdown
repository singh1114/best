---
title: Basic Introduction to Node.js Async Await
date: 2019-05-03 22:23:00 Z
categories:
- javascript
tags:
- javascript
author: Ranvir Singh
comments: true
layout: post
---

Async-Await has brought something awesome to the table. Prior to Promises, people always relied on `callbacks` for accomplishing those asynchronous tasks. Promises came to save the day with `.then` and async-await made it a whole lot easier.

<img alt="Image by HTML and js code by Ilya Pavlov from unsplash" src="https://images.unsplash.com/photo-1461749280684-dccba630e2f6?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=crop&amp;w=800&amp;q=60" style="height:467px; width:700px"/>

Hey there,
 
> Have you encountered a situation while writing JS code when you say, Why is the output of line 90 coming before the output of line 30.

Welcome back to yet another blog post. Today we are going to dive into one of the most talked subjects in the case of Node.js i.e. Async-Await.

Being a python( mostly synchronous) programmer, my understanding of the asynchronous world was quite limited. Until I was forced to write things in Node.js and I won't lie, I didn't like it in the beginning. But after spending quite some time with it, I can say that it is making sense now.

&nbsp;

Before diving right into the topic, we have to know about some of the history involved. Callbacks were the first things that were described as the life saviors a few years ago. But soon, people started feeling like the code was becoming too complex. Promises were the next big thing. But, it's hard to understand and make sense of some of the stuff involved. Also, the learning curve of Promises is quite steep.

Although Under the hood, Promises are being used in Async-Await, it almost gives you a feeling that you are writing a function in Python or any other language. I personally like this particular format of writing an Async function.

```javascript
const add = async function(a, b) {
    return a + b;
}
```

Inside an async function, you can use the await keyword to make a synchronous call and wait for the result. This is equal to using then in a promise.&nbsp;

```javascript
add(1, 2)
    .then(function(value) {
       console.log(value); 
});
```


This is equal to

>  
> 
>     
>     
>     await add(1, 2);
> 
> 
&nbsp;

But keep in mind to call await only in an async function. __The task of the await keyword is to stop the flow until the Promise is resolved.&nbsp;__This can sometimes lead to a bad position.&nbsp;

&nbsp;

There are some cases when all the function calls are mutually exclusive and are not related to each other. In that case, using PromisifyAll is a good solution. This will help you to reduce time wastage within the function.

&nbsp;

### __Handling Errors__

Handling errors are also very easy and feel very much pythonic with async await functions. You can run the try-catch block of all the functions individually.

&nbsp;
>  
> 
>     
>     
>     const add = async function (a, b) {
>         try {
>              return a + b;
>         } catch {
>              // Do something!
>              raise new Error("Some error!")
>         }
>     }
> 
> 

In the end, I just want to say that, making use of Promises is always going to be a little bit faster than async-await, But I personally like the async-await because they provide far more clarity of the code to the person who is new to the async world of JavaScript.

Please, leave your thoughts below. Which syntax you like and why?