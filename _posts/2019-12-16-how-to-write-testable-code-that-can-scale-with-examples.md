---
title: What have I learned about testing as a full-stack developer
published: true
date: 2019-12-16T00:00:00.000Z
image: 'https://i.imgur.com/OQXgcRy.jpg'
tags:
  - testing
  - python
  - javascript
  - webdev
categories:
  - testing
  - python
  - javascript
  - webdev
canonical_url: >-
  https://blog.soshace.com/follow-these-guidelines-to-write-testable-code-that-can-scale-with-examples/
---
I have seen people writing code which is hard to test and later writing tests just for the sake of it. Although having some tests is better than having no tests, you should not be writing tests just to increase the test coverage of the code. In this post, we will be discussing the ways which will help you to write testable code.

![How to write testable code that can scale](https://i.imgur.com/OQXgcRy.jpg "How to write testable code that can scale")

The responsibility of a Software Engineer is not only to deliver the software that works but also to deliver the software which is testable and maintainable. By maintainable, I mean any new person can come in and start writing the code from day one.

Most people don't like to test the code they write. There can be multiple reasons for that but almost 90% of the time it happens because the code is highly coupled with one another and programmers don't really know what should they check for in the tests.

The first time I was introduced to test-driven development when I was writing code for my [Google Summer of Code Project.](https://ranvir.xyz/blog/gsoc_2017/) My first impression of the TDD( Test-driven development) was not a very pleasant one. I would write the software with a great sense of pride but when it came to testing, I tried ways to escape it.

Why would someone write tests that were so dumb was the question in my mind. But as soon as I realized the importance of these test suite, I have never written any piece of code which is not tested( Scripts excluded).

The first step toward writing clean code, you need to write code that is differentiable on the basis of there usage. And the first step toward writing differentiable code is to think in terms of writing code that can be tested.

If we take a simple example of the library management system, the user module should not know anything about the book module and the book module should not know what is the time span for which the book is issued for.

Why most of the MVC( Model View Controller) frameworks win in this case is because they allow you to differentiate your code on the basis of what they do.

For example: If we take an example of the directory structure that a Python-based web framework, Django follows the following guidelines,

* You can write all your database related stuff in `models.py` files.
* You can write all URL related stuff in `urls.py`.
* You can write your app-specific logic in the `views.py`.

Although you can divide them further( and you should) according to the size of your application, this type of structure gives you a starting point and help you to choose which part of the code should go where.

If you want to write a `pre-save` hook for one of your tables which will add something to your table following some guidelines before the actual write happens in the database, you can simply argue that this part of code will definitely go to the model file.

## Some important terms

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
3. Write a test as you write the code.

### Using TDD

TDD or test-driven development is the type of testing in which you write test cases prior to writing any code for the software or according to [Uncle Bob](https://blog.cleancoder.com/), no incoming code should be merged into the main code before at least one failing test is written for that incoming part of code.

Although this is an awesome way of writing software leading to code without obvious errors, this significantly slows down the development time when you are starting out.

### Using the help of a tester

A tester is a person for whom the software is a black box and most of the time, he/she doesn't know about how the software works internally.

He/She is given a set of conditions each time any change is made to the code. Only after a tester gives a go through to the changes, the changes are merged.

Although you should always have one tester, you should not be solely dependent on this person.

### Writing tests as you go forward

Write code for something and write test cases to verify the changes that you have made taking into account the various conditions given by the business is one of the best and most widely used ways to verify that your software works.

All you need is to use any of the Continuous integration tools. You can use any of the tools out there. I personally have used [Travis CI](https://travis-ci.org/) and [Circle CI](https://circleci.com/). Both of them work pretty well.

### Unit testing

Unit testing is a way to test a single unit of software. For example, testing a utility function that changes the `Array/List` of characters to a string. Unit testing is the best way to be sure that your functions work as expected.

### Integration testing

Integration testing is a type of testing where you test a few units together. For example testing login, buying a product and checking out, the whole process in a single test.

A lot of people prefer a combination of both unit and integration tests for there codebase and its preferred to have at least API level integration testing.

It's very important to have these tests if you have 3rd party stuff in your codebase. Generally, people tend to mock these 3rd party calls and make sure that stuff works properly.

### Functional Testing

It is the type of testing, where you are testing something like a black box. If you are building a web application, it would mean to call the services via HTTP calls rather than making simple method calls using the application.

### What do we test for?

In the testing suite, we give a sample input to a given function and check if the function returns something which is expected or return something which is not expected.

`test_create_string.py`

```python
def create_string(char_list):
    return ''.join(char_list)

def test_create_string():
    abc = ['a', 'b', 'c']
    assert 'abc' == create_string(abc)
```

Run the command `py.test` to find if the test passes or fails. (By the way, you will have to install pytest before running this, use the command `pip install pytest`)

`1 passed in 0.02s` - I got this response. This means the test passed for me. You can also do negative assertions that can tell you that output is not a bad one.

Or in JavaScript,

```javascript
const assert = require('assert');

const createString = (charList) => {
    return charList.join('');
}

describe("createString", function() {

    it("Checks if the createString appends the characters properly.", function() {
        assert.equal(createString(['x', 'y', 'z']), 'xyz');
    });

});
```

You will have to install `mocha` for this. Mocha is used for testing code in JavaScript.

Install it using `npm install mocha`. Then run the command to test the file.

`mocha test_create_string.js`

You will get the following output if your test passes.

```bash
createString
✓ Checks if the createString appends the characters properly.

1 passing (17ms)
```

## Why Test your code

Testing your code has a lot of advantages few of them are discussed here. Testing always gives you confidence in the code that you write. These silly tests will be helpful in the later stages of development when you want to change something in the code.

### Become future proof

Writing test make your code future proof. Each code change will go through a test suite which will make sure that everything is working perfectly.

Let's say you want to add the functionality in the earlier function.

You want the function to return the parameter if the `type` of the parameter is not List/Array.

In Python

```python
def create_string(char_list):
    if type(char_list) == list:
        return ''.join(char_list)
    return char_list
```

or JavaScript

```javascript
const createString = (charList) => {
    if (Array.isArray(charList)) {
        return charList.join('');
    } else {
        return charList;
    }
}
```

All you have to do is add new tests to check if the new functionality is working or not. You will not have to worry about the earlier features.

Automated tests save us from regressions like accidental removal/ breakage of the old feature.

### Allow new joiners to write the code as quickly as they join

The new joiners can start working on your software as quickly as they join in. They can run the test suite to know more about the codebase.

> Test suite can work as the documentation of the codebase.

The new people don't have to worry about breaking something by the change they make.

### Make changes quickly

When you are backed by a lot of tests, you can start making changes quickly. All you have to do is to write tests for the new thing that you are trying to build.

You can go back to the module for which you changing the codebase and quickly check the current behavior by running the tests, write your changes with new tests and boom! You are done.

Tests give you fast feedback when building new features and changing old ones. Automated tests are far quicker than manual tests and can be repeated every time we want a new build of our application.

### Feel more confident in the changes that you make

This is the biggest achievement that tests give you as a developer. I myself have used the term like, `This module is thoroughly tested, we don't have to worry about it breaking`.

This much confidence can only come if your code is backed by a lot of good quality tests.

## What makes your code testable

Writing testable code is an art. Differentiating the testable code from a non-testable one is very important. Mixing them up leads to a mix up of code that you can't test.

### Write cleaner function

Well, the first and foremost thing that you can start doing is to start writing cleaner functions. I have written an article on [How to write clean function.](https://ranvir.xyz/blog/how-to-write-clean-functions-with-python-examples/). Hope this article will help you to write cleaner functions.

When you start writing a function that does only one thing, you will end up with the codebase which is entirely testable. You can simply write unit tests for all the functions separately.

### SOLID principles

Uncle Bob's SOLID principles teach us a lot about writing clean code that is testable.

According to [SOLID principles](http://butunclebob.com/ArticleS.UncleBob.PrinciplesOfOod), your code should follow the following guidelines.

**Single Responsibility Principle**

A class should have one and only one reason to change.

**The Open closed Principle**

You should be able to extend a classes behavior, without modifying it.

**The Liskov Substitution Principle**

Derived classes must be substitutable for their base classes. This means that functions that use references to base class must be able to use objects of derived class without knowing it.

**The Interface Segregation Principle**

Interfaces( A class which is only declared but the functionality is not defined, Functionality is defined in every extended class separately) must be fine-grained and should be client-specific.

**The Dependency Inversion Principle**

Depend on abstractions, not on concretions. That is, the modules that encapsulate high-level policy should not depend upon modules that implement details. For example, Your user module should not know, how the login is implemented.

### Make third party calls in separate modules

Third-party calls the main things which make your testing life a little bit difficult. You always have to mock these third party calls unless you really are performance testing something.

I have seen people writing a separate module for all these third-party calls. All you have to pass is the endpoint and credentials to use for making the call. It will spit out the response without worrying about the details.

### Mocking/ Stubbing

Mocking/ Stubbing is the process in which you mock the third party call assuming that it is already implemented correctly and there would be no fault in the given part.

Read more about mocking on [Martin Fowler's website](https://martinfowler.com/articles/mocksArentStubs.html)

### Using Factories/ Faker for object initialization

A lot of your time while testing can go in initializing objects for testing. You can generate random objects using these [factories in Python](https://ranvir.xyz/blog/how-to-use-factoryboy-to-create-model-instances-in-python-for-testing/).

[Faker](https://github.com/marak/Faker.js/) is the javascript module that can do the same thing in JavaScript.

### Remove circular dependencies

Circular dependency is a state in which module 1 is required by module 2 and module 2 is required by module 1. This is a very bad state to be in and is against the Dependency Inversion Principle.

Almost all of the languages are pretty hard on disallowing circular dependencies from happening but still, you can use different techniques to do circular dependency.

You have to think about the structure of code again and preferably refactor some of your code.

### Minimize global declarations

Minimize the number of variables you define globally. After some time, it becomes pretty hard to find where the variable was initialized and how the value is set to what it is being set to.

Debugging anything related to a global variable is a real pain.

### Replace conditional statements with polymorphism

It's pretty hard to follow the conditional statements after some time. You can have different actions for the same class if the user belongs to a separate category. You can use Polymorphism to solve this problem.

Following up on the example of a library management system if the user is admin, he/she can see the book details and if the user is a simple one he/she won't be able to see the details.

A simple function which when passed with the object of admin user should return back the details whereas when passed with the simple user should raise an error.

## How to test your Software properly

There is a definite guideline on how you should build the CI pipeline for your project and encourage everyone in the team to write more tests. Let's discuss this pipeline.

### Write unit as well as integration tests

It's always good to have a combination of both unit tests and integration tests. Whenever you write a new feature write the test cases along with the code.

What I prefer is to write all the test cases in simple words and ask them to be verified by the stakeholders( the business guys and team members). Once all of them are verified, I write code to solve the problem.

Once this is done, I pick up all the test cases and write them down in the code to check if they are passing or not. A lot of times, tests tell you a lot of places where the code can break which you might not have thought of.

### Use a CI tool (Continuous Integration)

Once you write down the test cases, you need to integrate a CI tool that can run your tests whenever you create a Pull Request/ Merge Request.

The CI tool should be able to run your tests. GitHub allows you to stop someone from pushing the code if the tests fail. You can add such checks in the code to avoid any occurrences of accidentally pushing of code.

### Add total coverage checks

Add a total coverage check to find the total coverage of your test cases. Coverage is the percent of code that is covered under your test cases.

Adjust the amount of coverage to be increased each time you add new code to your codebase and never try to fudge with this number. Make it a habit not to push untestable code.

Hope you understood the purpose of the post and will write more and more test against your code.
