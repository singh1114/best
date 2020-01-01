---
layout: post
title: Basic Introduction to Node.js Async Await
date: 2019-05-03T22:23:00.000Z
published: true
tags:
  - javascript
categories:
  - javascript
---

Async-Await has brought something awesome to the table. Prior to Promises, people always relied on `callbacks` for accomplishing those asynchronous tasks. Promises came to save the day with `.then` and async-await made it a whole lot easier.

![Image by HTML and javaScript code by Ilya Pavlov from unsplash](https://images.unsplash.com/photo-1461749280684-dccba630e2f6?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=crop&amp;w=800&amp;q=60 "Image by HTML and javaScript code by Ilya Pavlov from unsplash")

> Have you encountered a situation while writing JS code when you say, Why is the output of line 90 coming before the output of line 30.

Welcome back to yet another blog post. Today we are going to dive into one of the most talked subjects in the case of Node.js i.e. Async-Await.

Being a python( mostly synchronous) programmer, my understanding of the asynchronous world was quite limited. Until I was forced to write things in Node.js and I won't lie, I didn't like it in the beginning. But after spending quite some time with it, I can say that it is making sense now.

Before diving right into the topic, we have to know about some of the history involved. Callbacks were the first things that were described as the life saviors a few years ago. But soon, people started feeling like the code was becoming too complex. Promises were the next big thing. But, it's hard to understand and make sense of some of the stuff involved. Also, the learning curve of Promises is quite steep.

## Concurrency

Concurrency is something when we want to run a few things in parallel i.e. running a few tasks in the CPU at same instance as of other tasks.

### Why is concurrency important?

Concurrency is important in cases when the CPU is waiting for an I/O operation, or the response from an API or some kind of disk reads and writes.

Languages are designed to handle these types of concurrency problems in two ways,

* Synchronous: Blocks the context from going forward and wait for I/O operation which is easy to write and understand.
* Asynchronous: Doesn't block the context and allows the program to move forward and we can come back once the process is done. It is Hard to track the flow in following languages. JavaScript does belong to this category.

## Callbacks in JavaScript

As discussed, Historically, JavaScript has been handling this asynchronous behaviours using the `callbacks` which basically means calling a function when the task is complete.

```javascript
const callbackFunc = function (callback) {
    setTimeout(() => callback(null, "done"), 1000);
}

callbackFunc(function(err, result) {
    console.log(result)
})
```

### Benefits of using callbacks

* Low overhead, All you are doing is calling a function when something is done.
* We can do almost any asynchronous task using callbacks.

### Disadvantages of using callbacks

* Soon after using it for some time, people started realising that it is not a good practice to use callbacks as it makes your code far less readable. This term in JavaScript is known as [callback hell.](http://callbackhell.com/)
* Error handling is much of a pain in the callbacks.
* Difficult to understand for a person having a background in any other language like Java, Python.

Taking an ajax example,

```javascript
function getResponse () {
    let responseData;
    $.get('https://api.twitter.com/user/ranvirsingh1114', (response) => {
        responseData = response.data;
    });
    return responseData;
}

const response_data = getResponse();
console.log(responseData);
```

**Response:** `undefined`

This never works because the variable responseData is returned far before then the response of the request came.

## Promises in JavaScript

Promises are thin abstraction around callbacks to save you from some of the cons of the callbacks. [JavaScript info](https://javascript.info/promise-basics) have written a good post explaining promises.

Promise is an Object in JavaScript which is fulfilled sometime in future in JavaScript. A promise object can have any of the three states at any given time.

* Pending
* Resolved/ Fulfilled
* Rejected

```javascript
const promise = new Promise(function(resolve, reject) {
  setTimeout(() => resolve('Finished'), 1000);
});
```

In the beginning, the promise will be in the `Pending` state. After the promise is resolved you can see it going in the `Fulfilled` state.

### Benefits of Promises over callbacks

#### Chaining Promises

You can chain the Promises together without increasing the complexity of the code.

```javascript
promise = new Promise((resolve, reject) => {
    resolve(100);
}

const result = promise
    .then((result) => {
        return result + 100;
    }).then((result) => {
        return result - 200;
    }).then((result) => {
        console.log(result);
    })
```

**Response:** `0`

#### Error Handling

```javascript
const reslt = promise
    .then((result) => {
        return result + 100;
    }).then((result) => {
        return result - 200;
    }).catch(error => {
        throw new Error(error);
    })
```

For a given Promise, we only have to catch the errors only one time.

### Introducing parrallelism

You can use `.then` to introduce parrallelism by using something like `Promise.all(promises)`. This is particularly useful when you want to run similar process on a list of data.

## Async-Await in JavaScript( Removing then/ catch keywords)

Although Under the hood, Promises are being used in Async-Await, it almost gives you a feeling that you are writing a function in Python or any other language. I personally like this particular format of writing an Async function.

### How is Async-Await achieved?

Async-Await is achieved by combining the concepts of `Promises` and `Generators`. What we really do is stop the execution of the particular function and allow event-loop do its other stuff.

### Does it block the event-loop?

No it doesn't block the event-loop, it just stops the execution of the given `async` function and allows event-loop to do its own stuff.

```javascript
const add = async function(a, b) {
    return a + b;
}
```

Inside an async function, you can use the await keyword to make a synchronous call and wait for the result. This is equal to using then in a promise.

```javascript
add(1, 2)
    .then(function(value) {
       console.log(value);
});
```

This is equal to

`await add(1, 2);`

But keep in mind to call await only in an async function. `The task of the await keyword is to stop the flow until the Promise is resolved.` This can sometimes lead to a bad situations.

There are some cases when all the function calls are mutually exclusive and are not related to each other. In that case, using `PromisifyAll` is a good solution. This will help you to reduce time wastage within the function.

## Handling Errors with JavaScript Async-Await

Handling errors are also very easy and feel very much pythonic with async await functions. You can run the try-catch block of all the functions individually.

```javascript
const add = async function (a, b) {
    try {
       return a + b;
    } catch {
       // Do something!
       raise new Error("Some error!")
    }
}
```

In the end, I just want to say that, making use of Promises is always going to be a little bit faster than async-await, But I personally like the async-await because they provide far more clarity of the code to the person who is new to the async world of JavaScript.

Please, leave your thoughts below. Which syntax you like and why?
