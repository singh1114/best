---
title: Apply These Secret Techniques to write clean functions | With Examples
date: 2019-05-01 10:52:00 Z
categories:
- python
- clean-code
- JavaScript
tags:
- Python
- Clean-Code
- JavaScript
author: Ranvir Singh
comments: true
layout: post
---

I bet you have, every once in awhile, gone through a small piece of code trying to figure out that why was the given function written in a way it is written. Almost all companies have this service which just works and nobody wants to touch it and most of the time it is due to the bad way in which the code was written.

In this post, we are going to talk about writing clean functions and eventually reducing the technical overhead.

<img alt="" src="https://images-na.ssl-images-amazon.com/images/I/515iEcDr1GL._SX385_BO1,204,203,200_.jpg" style="height:499px; width:387px"/>

A few days ago I went through a book called, **Clean code**. Although I was not able to complete the full book, I was able to go through a few of the chapters one of which was,

**How to write clean functions.**

Here are the learnings of the chapter.

## Functions should not be large.

Functions should not be bigger than a few lines. Keeping a rule of thumb is to disallow a function bigger than 100 lines of code. Generally, functions should be even smaller than 10 lines.

## Creating blocks and proper indentation is very helpful.

Proper indentation and usage of blocks will take to long-distance while programming in a production system. Although this part is very much imposed in Python but keeping a style guide for a company is a good way to go.


```javascript
const function = makeChanges() {
const a = 10;
 const b = 20;
  return a + b;
  }
```

```javascript
const function = makeChanges() {
  const a = 10;
  const b = 20;
  return a + b;
}
```

You can feel the difference in the above examples.

    
## Every function should do only one thing.

Generally speaking, a function should only do one thing which should be self-explanatory from the name of the function. You should never stop yourself from writing longer names for your function if it self-explains itself.
    
## We should not be able to divide a function into sections.

Another way to put in that a function should generally be doing only one thing.
    
## One level of abstraction in all functions: Single level of a loop or if/switch statements.

The level of abstraction is something that a lot of people miss out on. Simply speaking the level of abstraction is the count of nested if statements/ loops that you use inside a function.

The number should be generally kept at a lower value.
    
## The code must be read from top to bottom.

I know this is hard for a number of people. Initially, even I used to follow the opposite rule. But after reading the book, I was able to reason this.

While reviewing the code people tend to start from the top slowly move toward the end. So it makes sense to start everything from the top and move down as you keep writing it.
    
## Switch statements should be avoided.

It's good to avoid `switch` statements as much as you can. Better to use `dict`( Python), `Map`/ `Object` (Javascript).


```javascript
const monthObj = {
  jan: function_1,
  feb: function_2,
  mar: function_3
};

const month = 'jan';

monthObj[month]();
```

```python
month_obj = {
  'jan': function_1,
  'feb': function_2,
  'mar': function_3
};

month = 'jan';

monthObj[month]();
```

Although sometimes it's hard to change switch statements to something like this. Always prefer readability over speed if the differences in the speed are not that large.
    
## Use descriptive names.

We have already discussed this. We should always choose better names for the functions. Descriptive names will go a long way rather than some random docstring for the function.
    
## A lesser number of function arguments should be there.

The number of arguments should be lower. And if you are writing the class method, better to make it an instance variable.
    
**Note: Try to avoid flag arguments. This means function does more than one thing.**
    
## Monadic function

Function with one argument. Always try to write Monadic functions whenever possible.
    
## Dyadic function

Function with two arguments
    
## Triads

Functions with three arguments. Try not to write as much as possible. It's better to wrap those arguments in their own class if the number of arguments starts increasing a given number.

For example:

converting,

```python
makeCircle(x, y, radius)
```

to

```python
makeCircle(center, radius)
```
where a center is an object of the class Centre, makes a lot of sense.

# Naming Conventions:

__For monads__: Choose a combination of verb + noun:

Example: `writeField(name)`, explains that name is written to a field.

Also, function name `assertEquals(expected, actual)` can be changed to `assertExpectedEqualsActual(expected, actual)`, which makes more sense.

## Have no side effects

Side effects mean changing the value of the class argument/ Global argument/ passed argument. All these types of changes must be avoided.

For example: Say you have a function called `checkUserPassword(userName, password)` and in the same function you are initializing the session for the user, then the function can only be used in certain instances( when the user is trying to log in, not at a time when the user wants to change the password). This coupling is also called temporal coupling. A good idea is to change the name of the function and specify that the function has temporal coupling.

Example: `checkPasswordAndInitializeSession(userName, Password)`

## Functions should either do something or answer something but should never do both. 

This is called Command Query Separation.
 
## Prefer raising exceptions rather than returning error codes.

## Extract the bodies of the `try-catch` statements into functions.
    
Example:

```python
try:
   trythisfunc();

except:
   logError(); // this function do only error logging.
```

## DRY: Don’t repeat yourself.
    
**Note: One great idea is to write long and bad function first, then writing tests for every line of code. Then refining the code and still not allowing the tests to fail.**

I hope you liked some of the points over there. Also, there might be a few things that you don't agree upon. Do share them in the comment section of this post.

You can buy the book from here:

<a href="https://www.amazon.in/gp/product/935286512X/ref=as_li_tl?ie=UTF8&amp;camp=3638&amp;creative=24630&amp;creativeASIN=935286512X&amp;linkCode=as2&amp;tag=rangerranvir-21&amp;linkId=504b1b7e6b0016856271b15e11098cb7" target="_blank">Clean Architecture: A Craftsman's Guide to Software Structure and Design</a><img alt="" src="//ir-in.amazon-adsystem.com/e/ir?t=rangerranvir-21&amp;l=am2&amp;o=31&amp;a=935286512X" style="height:1px; margin:0px !important; width:1px"/>