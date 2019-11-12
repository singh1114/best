---
title: Apply These Secret Techniques to write clean functions | Python Examples
date: 2019-05-01 10:52:00 Z
author: Ranvir Singh
comments: true
layout: post
---

<img alt="" src="https://images-na.ssl-images-amazon.com/images/I/515iEcDr1GL._SX385_BO1,204,203,200_.jpg" style="height:499px; width:387px"/>

A few days ago I went through a book called, Clean code. Although I was not able to complete the full book, I was able to go through a few of the chapters one of which was, __How to write clean functions.__

Today I am going to share what I have learned with you guys.


* Functions should not be large.  
    
* Creating blocks and proper indentation is very helpful.
    
* Every function should do only one thing.
    
* We should not be able to divide a function into sections.
    
* One level of abstraction in all functions: Single level of a loop or if/switch statements.
    
* The code must be read from top to bottom.
    
* Switch statements should be avoided.
    
* Use descriptive names.
    
* A lesser number of function arguments should be there. Better to make-instance variable.
    
* Try to avoid flag arguments. This means function does more than one thing.
    
* Monadic function: Function with one argument
    
* Dyadic function: Function with two arguments
    
* Triads: Functions with three arguments.
    
* What to do when arguments are more than this: It's better to wrap those arguments in their own class.

For example:

```
makeCircle(x, y, radius)
```

```
makeCircle(center, radius)
```

Where a center is an object of the class Centre.

__Naming Conventions:__

__For monads__: Choose a combination of verb + noun:

Example: `writeField(name)`, explains that name is written to a field.

Also, `assertEquals(expected, actual)` can be changed to `assertExpectedEqualsActual(expected, actual)`, which makes more sense.

__Have no side effects:__

Side effects mean changing the value of the class argument/ Global argument/ passed argument. All these types of changes must be avoided.

For example: Say you have a function called `checkUserPassword(userName, password)` and in the same function you are initializing the session for the user, then the function can only be used in certain instances( when the user is trying to log in, not at a time when the user wants to change the password). This coupling is also called temporal coupling. A good idea is to change the name of the function and specify that the function has temporal coupling.

Example: `checkPasswordAndInitializeSession(userName, Password)`

* Functions should either do something or answer something but should never do both. This is called Command Query Separation.
 
* Prefer raising exceptions rather than returning error codes.

* Extract the bodies of the `try-catch` statements into functions.
    
Example:

```
> try {
> 
>    trythisfunc();
> 
> }
> 
> Catch (Exception e) {
> 
>    logError(); // this function do only error logging.
> 
> }
```

* DRY: Don’t repeat yourself.
    
* One great idea is to write long and bad function first, then writing which tests every line of code. Then refining the code and still not allowing the tests to fail.

I hope you liked some of the points over there. Also, there might be a few things that you don't agree upon. Do share them in the comment section of this post.

You can buy the book from here:

<a href="https://www.amazon.in/gp/product/935286512X/ref=as_li_tl?ie=UTF8&amp;camp=3638&amp;creative=24630&amp;creativeASIN=935286512X&amp;linkCode=as2&amp;tag=rangerranvir-21&amp;linkId=504b1b7e6b0016856271b15e11098cb7" target="_blank">Clean Architecture: A Craftsman's Guide to Software Structure and Design</a><img alt="" src="//ir-in.amazon-adsystem.com/e/ir?t=rangerranvir-21&amp;l=am2&amp;o=31&amp;a=935286512X" style="height:1px; margin:0px !important; width:1px"/>