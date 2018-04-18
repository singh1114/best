---
author: Ranvir Singh
comments: true
date: 2018-04-17 19:57:59.564352
layout: post
title: Working properly with Django Choices
slug: working-properly-with-django-choices
---
Implementing Django choices in models is not very sophisticated. While writing models you expect that you might be looking neat fields that are used to store data. But when you introduce choices in Django it becomes cumbersome. Django choices are written as tuples inside tuples. A simple example of such thing can be the fancy animal problem.

    
    
    animal = (
        ('cat', '0'),
    	('lizard', '1'),
    	('dog', '2'),
    )
    animal_type = models.CharField(choices = animal, max_length = 2)

&nbsp;

animal\_type is the only data that is going to be stored in the database. For that, we wrote a lot of extra things in the model&nbsp;file.&nbsp;

If you are using python version greater than 3.4. You can make something with the enum. But if you are using anything below than 3.4 you have to use some other implementation.&nbsp;

This one looked good to me on the first look. The documentation showed every possible use case.

<https://github.com/bigjason/django-choices>

You can use this module as follows.&nbsp;

    
    
    
    # choices.py
    from djchoices import DjangoChoices, ChoiceItem
    
    class PersonType(DjangoChoices):
        customer = ChoiceItem("C")
        employee = ChoiceItem("E")
        groundhog = ChoiceItem("G")
    
    
    # models.py
    
    from .choices import PersonType
    
    class Person(models.Model):
        type = models.CharField(max_length=1, choices=PersonType.choices)
    

Hope you find this useful.