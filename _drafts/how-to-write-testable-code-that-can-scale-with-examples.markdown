---
title: How to write testable code that can scale | With Examples
date: 2019-11-20 17:44:00 Z
---

I have seen people writing code which is hard to test and later writing tests just for the sake of it. Although having some tests is better than having no tests, you should not be writing tests just to increase the test coverage of the code. In this post, we will be discussing the ways which will help you to write testable code.

The responsibility of a Software Engineer is not only to deliver the software that works, but also to deliver the software which is testable and maintainable. By maintainable, I mean any new person can come in and start writing the code from day one.

Most people don't like to test the code they write. There can be multiple reasons for that but almost 90% of the time it happens because the code is highly coupled with one another and programmers don't really know what should they check for in the tests.

The first time I was introduced to test-driven development when I was writing code for my [Google Summer of Code Project.](https://ranvir.xyz/blog/gsoc_2017/). My first impression of the TDD( Test-driven development) was not a very pleasant one. I would write the software with great sense of pride but when it came to testing, I tried ways to escape it.

Why would someone write tests that were so dumb was the question in my mind. But as soon as I realized the importance of these test suite, I have never written any piece of code which is not tested( Scripts excluded).

The first step toward writing clean code, you need to write code that is differentiable on the basis of there usage. And the first step toward writing differentiable code is to think in terms of writing code that can be tested.

If we take a simple example of the library management system, the user module should not know anything about the book module and the book module should not know if what is the time span for which the book is issued for.

Why most of the MVC( Model View Controller) frameworks win in this case is because they allow you to differentiate your code on the basis of what they do.

For example: If we take an example of the directory structure that a Python-based web framework, Django follows,

* You can write all your database related stuff in `models.py` files.

* You can write all URL related stuff in `urls.py`.

* You can write your app-specific logic in the `views.py`.

Although you can divide them further according to the size of your application, this type of structure gives you a starting point and help you to choose which part of the code should go where.

If you want to write a `pre-save` hook for one of your table which will add something to your table following some guideline will definitely go to the model file.

## Some terms

### Software testing

Software testing is a procedure in which software is tested for bugs and off behaviors that were not inserted intentionally.

For a given library management software we can check for the following test cases.

1. At any time admin should be able to find which books are issued to which users.
2. At any time admin should be able to find which books are present in which part of the library hall.
3. At a given time, admin should be able to find the fine payable by a given user.
4. At a given time, the admin should be able to issue a book to the user.
5. At a given time, a user should be able to return the book to the library.

These are a few test cases that will be generated and shared among the stack holders who are working on the project.

Now, there are a few ways to test the software once it is done.

1. Use TDD.
2. Use the help of a tester.
3. Write a test as you move forward with the code.

### Using TDD

TDD or test-driven development is the type of testing in which you write test cases prior to writing any code for the software or according to [Uncle Bob](https://blog.cleancoder.com/), no incoming code should be merged into the main code before at least one failing test is written for that part of code.

Although this is an awesome way of writing software leading to code without obvious errors, this significantly slows down the development time when you are starting out.

### Using the help of a tester

A tester is a person for whom the software is a black box and most of the time, he/she doesn't know about how the software works internally.

He/She is given a set of conditions each time any change is made to the code. Only after a tester gives a go through to the changes, the changes are merged.

### Writing tests as you go forward

Write code for something and write test cases to verify the changes that you have made taking into account the various conditions given by the business is one of the best and most widely used ways to verify your software quickly.

All you need is to use any of the Continuous integration tools. You can use any of the tools out there. I personally have used [Travis CI](https://travis-ci.org/) and [Circle CI](https://circleci.com/). Both of them work pretty well.

### Unit testing vs Integration testing

## Why Test your code

Testing your code has a lot of advantages few of them are discussed here.

### Become future proof

Writing test make your code future proof. Each code change will go through a test suite which will make sure that everything is working perfectly.

### Allow new joiners to write the code as quickly as they join

### Make changes quickly

### Feel more confident in the changes that you make

## What makes your code testable

### Write cleaner function

### SOLID principles

### Make third party calls differently

### Law of Demeter

### Using Factories for object initialization

### Stop circular dependencies

## How to test your Software properly

### Write unit as well as integration tests

### Use a CI tool (Continuous Integration)

### Add total coverage check before merging the code