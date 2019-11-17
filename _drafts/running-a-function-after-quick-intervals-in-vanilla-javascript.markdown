---
title: Running a function after quick intervals in Vanilla JavaScript
date: 2019-11-17 19:34:00 Z
categories:
- javascript
- programming
tags:
- javascript
- programming
---

In this post, I am simply going to talk about a simple script that we are going to use which will run itself after some consequent time periods.

```javascript
var minutes = 15, interval = minutes * 60 * 1000;
setInterval(function() {
    console.log("I am doing my 5 minutes check");
    main().catch(console.log);
}, interval);
```