---
title: Working properly with Django Choices
date: 2018-04-17 19:57:00 Z
categories:
- python
- django
tags:
- python
- django
author: Ranvir Singh
comments: true
layout: post
---

The default implementation of choices in Django is not very intuitive and we repeat a lot of code while using them. 

While writing models you expect that you might be looking at neat fields that are used to store data. But when you introduce choices in Django it becomes cumbersome.

By default, Django choices are written as tuples inside tuples. A simple example can be a fancy animal problem.

    
```
animal = (
    ('cat', '0'),
    ('lizard', '1'),
    ('dog', '2'),
)
animal_type = models.CharField(choices=animal, max_length=2)
```

`animal_type` is the only data that is going to be stored in the database. For that, we wrote a lot of extra things in the model file.

If you are using a Python version greater than `3.4`. You can make something with the enum and create a very sophisticated version of your own, but if you are using anything below `3.4` you have to use some other implementation.

This one looked good to me on the first look. The documentation showed every possible use case.

<https://github.com/bigjason/django-choices>

You can use this module as follows.&nbsp;

```   
    # choices.py
    from djchoices import DjangoChoices, ChoiceItem
    
    class PersonType(DjangoChoices):
        customer = ChoiceItem("C")
        employee = ChoiceItem("E")
        groundhog = ChoiceItem("G")
```    
   

While in the models file.

``` 
    # models.py
    
    from .choices import PersonType
    
    class Person(models.Model):
        type = models.CharField(max_length=1, choices=PersonType.choices)
``` 

This way you can differentiate the implementation of the choices and database implementation separate. The only downside of using this is updating the real choice values in the future. You have to write a custom migration to make those changes live.

Hope you find this useful. Share this on social media and let others know about this awesome library.