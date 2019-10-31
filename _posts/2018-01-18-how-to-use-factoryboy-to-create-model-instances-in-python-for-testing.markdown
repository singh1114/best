---
title: How to use FactoryBoy to create model instances in python for testing
date: 2018-01-18 18:43:00 Z
categories:
- Django
- Python
- FactoryBoy
- Technology
- Testing
author: Ranvir Singh
comments: true
layout: post
---

Testing is one of the basic and most important part of the development process that is needed to be done every time you write code.

I have already discussed testing in one of my earlier posts. In that post, I will talk about the way in which we can write tests for models.

For testing models, we need to create sample objects for this.

It's pretty hard to write the same code again and again to create same object.

Today I am going to talk about using FactoryBoy for testing Django application.

The name **FactoryBoy** is inspired by the Factory Girl testing tool for Ruby on Rails. Without Factory boy, you have to write a lot of code for the creation of test cases.

For writing test, you have to spend a lot of time writing the setup method for the tests.

Without the use of factories, this is how your tests will look like:

```python
from django.test import TestCase
from my_app.models import Person

class DataBaseStore(TestCase):
    def setUp(self):
        # Creating all the models   
        Person.objects.create(gender='male', age=20, name='ranvir')  
    
    def test_something(self):
        # test all the things that you want to.
        pass
```
 

On the other hand, it is always nice to separate your setting up `method` from the testing method. For this sometimes we have to write long code in the beginning which helps us in the future by allowing us to write smaller code in the future. 

We can write factories anywhere but it's always a good idea to write it in a file named factories.py inside the root directory of your app.

Write following in the factories.py file inside your root directory.

 
```python
from factory.django import DjangoModelFactory  
from my_app.models import Person  

class PersonFactory(DjangoModelFactory):  
    class Meta:  
        model = Person  
    name = 'ranvir'  
    age = 20  
    gender = 'male'  
```

Now we can simply call these factories during the test generation and create as many instances of models as we want to. This is a pretty simple case but we really can do a lot more. We can create instances of varies types by making use of FuzzyText and Sequence.

With the use of `FuzzyText`, you can generate random text making testing more awesome.

Testing is also considered as the sign of a good programmer. There are a ton of benefits of testing which were discussed in the [post](https://singh1114.github.io/blog/writing-unit-tests-for-the-models/).

I hope you guys liked the idea of the post. We really can do a lot of stuff using this library. Do share your views regarding this post if you have used factories in the past or want to use it in your project.
