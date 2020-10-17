---
layout: post
title: How to use FactoryBoy to create model instances in Django for testing
date: 2018-01-18T18:43:00.000Z
description: >-
  Using FactoryBoy to create model objects automatically for the purpose of
  testing.
published: true
author_name: Ranvir Singh
author_username: ranvir_xyz
canonical_url: https://ranvir.xyz/blog/how-does-django-validate-passwords/
tags:
  - testing
  - python
  - django
categories:
  - FactoryBoy
  - python
  - django
  - testing
---
Testing is one of the basic and most important parts of the development process that is needed to be done every time you write or change any part of the code. It gives you the authority confidence in the code that you are writing.

I have already discussed testing in one of my earlier posts.

{% include linked_post.html url="writing-unit-tests-for-the-models" %}

In this post, I will talk about the way in which we can write tests for models.

For testing models, we need to create sample objects.

It's pretty hard to write the same code again and again to create the same objects. 😱

Today I am going to talk about using [FactoryBoy](https://github.com/FactoryBoy/factory_boy) for testing Django application.

The name **FactoryBoy** is inspired by the Factory Girl testing tool for Ruby on Rails. Without Factory boy, you will have to write a lot of code for the creation of test cases.

For writing tests, you have to spend a lot of time writing the setup method for the tests.

## Creating model objects without FactoryBoy

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


On the other hand, it is always nice to separate your setting up `method` from the testing method. For this sometimes we have to write long code in the beginning which helps us in the future by allowing us to write smaller code.

We can write factories anywhere but it's always a good idea to write it in a separate file named factories.py inside the root directory of your app.

Write following in the `factories.py` file inside your root directory.

## Creating model objects with FactoryBoy

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

Now we can simply call these factories during the test generation and create as many instances of models as we want to. This is a pretty simple case but we really can do a lot more. We can create instances of varies types by making use of `FuzzyText` and Sequence.

With the use of `FuzzyText`, you can generate random text making testing more awesome.

## Applications of FactoryBoy

### Getting random values

We can get random values for the purpose we specify to the `Faker` method. The values created are far more realistic than any other random methods that we use otherwise.

```python
from factory import Faker

class PersonFactory(DjangoModelFactory):
    class Meta:
        model = Person
    name = Faker('name')
    age = 20
    gender = 'male'
```

Here is a list of [available providers by faker library](https://faker.readthedocs.io/en/stable/providers.html) which can be used.

### Reproducing random values

Sometimes our tests fail for some random value and not for all of them. So, `factory` have introduced a concept using which we can create the same value again and again.

```python
from factory.random import reseed_random

class PersonFactory(DjangoModelFactory):
    class Meta:
        model = Person
    name = reseed_random('Bill Clinton')
    age = 20
    gender = 'male'
```

### Using dependent values of other fields

There are some cases in which you want to use the values which are dependent on the random values of the other fields. For example, full name can be the combination of first and last name.

```python
from factory import Faker, LazyAttribute

class PersonFactory(DjangoModelFactory):
    class Meta:
        model = Person
    first_name = Faker('first_name')
    second_name = Faker('last_name')
    full_name = factory.LazyAttribute(lambda a: '{0} {1}'.format(a.first_name, a.last_name))
```

### Using sequences for unique fields.

With random function, there is a chance that after some time the values will start repeating, and if your test suite has grown out of that threshold size you will have to use sequences in your unique fields.

```python
from factory import Sequence

class PersonFactory(DjangoModelFactory):
    class Meta:
        model = Person
    email = Sequence(lambda n: 'person{0}@ranvir.xyz'.format(n))
```

### Foreign Keys

If your field is a foreign key, you can directly use that whole factory all together.

```python
from factory import Sequence

class PersonFactory(DjangoModelFactory):
    class Meta:
        model = Person
    email = Sequence(lambda n: 'person{0}@ranvir.xyz'.format(n))

class SocietyFactory(DjangoModelFactory):
    class Meta:
        model = Person
    society_number = Sequence(lambda n: 'Society {0}'.format(n))
    person = factory.SubFactory(PersonFactory)
```

Testing is also considered as the sign of a good programmer. There are a ton of benefits of testing which were discussed in the [post](https://ranvir.xyz/blog/writing-unit-tests-for-the-models/).

I hope you guys liked the idea of the post. We really can do a lot of stuff using this library. Do share your views regarding this post if you have used factories in the past or want to use it in your project. 😇
