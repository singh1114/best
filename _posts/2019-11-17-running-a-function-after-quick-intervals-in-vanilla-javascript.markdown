---
title: Run a function periodically in Javascript (with memory leak analysis)
date: 2019-11-17 19:34:00 Z
categories:
- javascript
- programming
- beginners
tags:
- javascript
- programming
- beginners
image: https://i.imgur.com/KX8Gign.jpg
---

In a production system, we run a lot of scripts periodically either to sync data from some third-party source or spit data to some source. Although there are a lot of solutions to achieve such periodic behavior, in this post we are going to discuss one such solution using vanilla JavaScript.

![Run a function periodically in JavaScript](https://i.imgur.com/KX8Gign.jpg "Run a function periodically in JavaScript")

## Use cases

* Taking backups of the database.

Taking a backup of the database can be done once or twice a day depending upon the use case. 

If you get a lot of users you can take this backup multiple times a day.

**AWS** takes automatic backups so you don't have to worry about it.

* Sending newsletters to your customers.

Sending newsletters to customers can also be one of the use cases of running things periodically.

## Possible Solutions

### Crontab

Most of the organizations tend to use crontab for handling any such requests for running periodic tasks.

Each and every language has it's own implementation of handling periodic tasks.

## Periodic task in Vanilla JavaScript

Let's write a simple function that can log the current time after every minute. Save this code in the file `time_tell.js`.

```javascript
const tellTime = async function () {
    console.log(new Date());
}

const minutes = 0.5;
const interval = minutes * 60 * 1000;

setInterval(function() {
    // catch all the errors.
    tellTime().catch(console.log);
}, interval);
```

First of all, we declare an `async` function `tellTime` which logs the time whenever it is called.

It is important to declare this function `async` so that we can run `.then` or `.catch` after this function.

`setInterval` is the inbuilt function that can run any statements after every given interval.

It takes two arguments, first is the definition of the function being run itself and next is the interval after which we want to run the function again( **In milliseconds**).

In this example, we have set the interval to one minute.

Run the file using the command,

`node time_tell.js`

Here is how the output is going to look like,

```javascript
2019-11-18T18:40:27.286Z
2019-11-18T18:40:57.293Z
...
```

Although this is a pretty straight forward example you can extend this to do anything that you want.

## Update regarding Memory leak

When I posted the same on [dev.to](https://dev.to/singh1114/run-a-function-periodically-in-vanilla-javascript-8gk), some of the programmers reached out in the comment section asking about the potential memory leak in the program.

While building the program, I was not thinking about the memory leak because I was going to run it for a few hours only for a particular use case.

I searched online to find a solution for finding ways to discover any memory leaks in the program. [This nearform article](https://www.nearform.com/blog/how-to-self-detect-a-memory-leak-in-node/) was very helpful in finding more about it.

The article suggested three ways to find out the memory leaks. I have only tried two of them. Let me know if you have any other way of finding it out as well.

### Node's inspect flag

Node's `--inpect` flag attaches a debugger with the program and allows you to run all types of analysis on the program running in the chrome.

Try running the following command.

`node --inspect time_tell.js`

This will open a new tab in the chrome with the attached debugger,

```
Debugger listening on ws://127.0.0.1:9229/2ee7271d-04e2-4711-9df5-99777bdb7ca4
For help see https://nodejs.org/en/docs/inspector

Debugger attached.
```

Go to the `memory` tab of the devtool in the chrome and click on the take snapshot button. You will be able to see the memory being used when you take the snapshot.

Take another snapshot after 10 seconds of the initial snapshot. If the memory size is increasing you will know that there is a function in your code which is leaking memory.

![Chrome memory leak analysis](https://i.imgur.com/Zyze7jE.jpg "Chrome memory leak analysis")

Since the memory used in the given program was consistent, I believe there was no memory leak in the program.

### Using memwatch-next module

The `memwatch-next` module is used to find the memory leaks in a program.

Let's install it using,

`npm install memwatch-next`

Now change the program accordingly,

```javascript
const memwatch = require('memwatch-next');

const tellTime = async function () {
    console.log(new Date());
}

const minutes = 0.01;
const interval = minutes * 60 * 1000;

setInterval(function() {
    // catch all the errors.
    tellTime().catch(console.log);
}, interval);

memwatch.on('leak', (info) => {
  console.error('Memory leak detected:\n', info);
});
```

Run the program simply, if you see the message memory leak being printed, you will know that there is some memory leak.

Hopefully, this will help you to find memory leaks in your program in the future as well.

Thanks for stopping by and do consider [subscribing](https://ranvir.xyz/blog/subscribe) to the weekly newsletter.