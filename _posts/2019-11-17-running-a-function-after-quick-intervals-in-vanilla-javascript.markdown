---
title: Run a function periodically in vanilla Javascript
date: 2019-11-17 19:34:00 Z
categories:
- javascript
- programming
tags:
- javascript
- programming
---

There are many cases in which someone will want to run something periodically. Although there are a lot of solutions to this problem, in this post we are going to discuss one such solution in detail which will involve vanilla JavaScript.

## Use cases

* Taking the backup of the database.

Taking a backup of the database can be done once or twice a day depending upon the use case. 

If you get a lot of users you can take this backup multiple times a day.

**AWS** takes automatic backups as well.

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

var minutes = 0.5, interval = minutes * 60 * 1000;
setInterval(function() {
    // catch all the errors.
    tellTime().catch(console.log);
}, interval);
```

Although this is a pretty straight forward example you can extend this to do anything that you want.