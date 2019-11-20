---
title: How to write testable code that can scale | With Examples
date: 2019-11-20 17:44:00 Z
---

I have seen people writing code which is hard to test and later writing tests just for the sake of it. In this post, we will be discussing the ways which will help you to write testable code.

The responsibility of a Software Engineer is not only to deliver the software that works, but also to deliver the software which is testable and maintainable.

Most of the people don't like to test the code because the code is highly coupled with one another and 

The first time I was introduced to test-driven development, I was writing code for my [Google Summer of Code Project.](https://ranvir.xyz/blog/gsoc_2017/). My first impression of the TDD( Test-driven development) was not a very pleasant one. I was trying out ways to escape that thing.

Why would someone write tests that were so dumb was the question in my mind. But as soon as I realized the importance of these test suite, I have never written any piece of code which is not tested( Scripts excluded).

The first step toward writing clean code, you need to write code that is differentiable on the basis of there usage. And the first step toward writing differentiable code is to think in terms of writing code that can be tested.

Why most of the MVC( Model View Controller) frameworks win in this case is because they allow you to differentiate your code on the basis of what they do.

For example: If we take an example of directory structure that a Python-based web framework, Django follows,

* You can write all your database related stuff in `models.py` files.
* You can write all URL related stuff in `urls.py`.
* You can write your app-specific logic in the `views.py`.

Although you can divide them further according to the size of your application, this type of structure gives you a starting point and help you to choose which part of the code should go where.

If you want to write a `pre-save` hook for one of your table which will add something to your table following some guideline will definitely go to the model file.

## Why 