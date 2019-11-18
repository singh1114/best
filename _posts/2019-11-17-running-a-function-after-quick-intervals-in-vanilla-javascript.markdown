---
title: Run a function periodically in vanilla Javascript
date: 2019-11-17 19:34:00 Z
categories:
- javascript
- programming
- beginners
tags:
- javascript
- programming
- beginners
---

There are many cases in which someone will want to run something periodically. Although there are a lot of solutions to this problem, in this post we are going to discuss one such solution in detail which will involve vanilla JavaScript.

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

Let's write a simple function that can log the current time after every minute.

```javascript
const tellTime = async function () {
    console.log(new Date());
}

const minutes = 1;
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

Here is how the output is going to look like

```javascript
2019-11-18T18:40:27.286Z
2019-11-18T18:40:57.293Z
...
```

Although this is a pretty straight forward example you can extend this to do anything that you want.