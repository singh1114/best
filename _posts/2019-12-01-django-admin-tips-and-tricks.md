---
title: Django admin tips and tricks
date: 2019-01-23T12:00:00.000Z
description: >-
  Django admin tips and tricks that you can use to create internal app for
  production ready system.
published: true
tags:
  - django
  - django-admin
  - python
categories:
  - django
  - django-admin
  - python
canonical_url: ''
---
Django is one of the best Python frameworks to get started with web development and get out with your product in no time. With Django, you don't have to worry about any of the things like security, databases or most importantly admin panel.

Django comes with a built-in admin panel that you can use any time of handling any type of internal work. This saves you a lot of development time and also saves you a lot of money as a company.

You can do everything that you can think of using the admin. Some companies start off just by creating their products using the default admin interface. It provides a very good level of users and permissions handling.

In this post, we are going to discuss some tips and tricks in which you can start using the Django admin in your production effectively.

Let's set up a simple project in Django and try to look at some of the admin related stuff.

## Setup up Django project

While we set up the Django project you will know how easy it is to set up a production-based system using this Python framework.

All you need is a working Python environment. For this sake of the tutorial, we are going to use Python 3+. I personally am using Python 3.7+. You can use virtual environments to use any of the new Python versions and keep using the old ones as well.

Here is an old post on [how to install a virtual environment on your Ubuntu machine.](https://ranvir.xyz/blog/how-to-install-django-using-virtual-environment/)

For Mac users, you can refer to any of the posts out there. [Here](https://evansdianga.com/install-pip-osx/) is one of them.

Once you install the virtual environment, you can apply the following command to create the virtual environment.

### Setting up the virtual environment

```shell
python3 -m venv venv
```

Once the creation of the virtual environment is done you can activate the virtual environment using the following commands.

```shell
source venv/bin/activate
```

You can verify that this process worked if you start getting the environment name behind the directory name in the shell.

```shell
(venv) ➜  ~Documents/soshace
```

Also you can confirm by checking the Python version.

```shell
python -V
```

You should be able to see the python version.

```shell
Python 3.7.4
```

If you want you can deactivate the virtual environment using the following command.

```shell
deactivate
```

### Starting the Django project

For the purpose of this tutorial, we will be creating a simple School management system with as simple as possible execution.

The first step involved is to install Django in the virtual environment. Django default setup comes with the inbuilt SQLite database, so you don't have to worry about that as well. That is enough for the purpose of the tutorial.

```shell
pip install django
```

Also, it is recommended to add the installed packages in a separate `requirements.txt` file so that anyone can copy your code and setup without going much in the detail. There is a command to help you with that as well.

```shell
pip freeze > requirements.txt
```

Then people can directly call this command to install all the dependencies.

```shell
pip install -r requirements.txt
```

To start the Django project, use the following command.

```shell
django-admin startproject schoolproject
```

This command will create a simple Django project with everything included. This will involve default admin system, default database migrations and many more things.

Now change the working directory to the project that you just created.

```shell
cd schoolproject
```

You will the `manage.py` file which will include all the runnable commands for Django. Run the following command to create the default tables in the database. Django sample project also creates the default migrations which will create all the required tables for you.

These migrations include one for the user table which we will use to log in to the admin system. Run the following command to create the tables

```shell
python manage.py migrate
```

For logging in to the admin system you will need to create a superuser.

```shell
python manage.py createsuperuser
```

This will prompt you to tell some simple stuff like username and password.

Once this is done you can start the Django server using the following command.

```shell
python manage.py runserver
```

This will start the server on the default port `8000`. The default admin page can be found on the `/admin` endpoint. Use the link `http://127.0.0.1:8080/admin` to land on the admin page.

Use the same credentials to log yourself in that you just set up a few seconds ago.

In a Django project, everything is handled using apps. You can create a simple app using the following command.

```shell
python manage.py startapp schoolapp
```

Include this newly created app in the settings file.

```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'schoolapp'
]
```

## Change the default admin address.

It is important to change the default admin address so that attackers have a good hard time getting to your admin page.

Change the following part of the code in the `schoolproject/urls.py` file.

```python
urlpatterns = [
    re_path('yourcompany/admin/', admin.site.urls),
]
```

Now you can see the admin page on `yourcompany/admin/` endpoint.

{% include lazyload.html image_src="https://i.imgur.com/l1MJHzP.png" image_alt="Django Admin login page" image_title="Django Admin login page" %}

## Change the default name of the admin web page

You can change the default heading and other things of the admin page to make it more personal for your brand.

You can do it in any of your apps. Generally, people create a default `base` app and do all kinds of such stuff in there.

Write this code in `schoolapp/admin.py`

```python
from django.contrib import admin

admin.site.site_header = 'MY SCHOOL APP'
admin.site.index_title = 'Your Company'
```

{% include lazyload.html image_src="https://i.imgur.com/Rgde88w.png" image_alt="Django admin page with custom title" image_title="Django admin page with custom title" %}

## Handling History/ Model Logs in Django admin panel

Django history is a simple extendible app in Django which you can use to your advantage and create awesome things with it.

For example storing more accurate data about the changes made in the Django admin panel.

For this, we first have to create the sample models in `schoolapp/models.py`.

```python
from django.db import models

class School(models.Model):
    school_name = models.CharField(max_length=30)
    address = models.CharField(max_length=30)
    principle_name = models.CharField(max_length=30)
```

Now run the command to `makemigrations`

```shell
python manage.py makemigrations
```

Now run the migrations to the database.

```shell
python manage.py migrate
```

Now register the new model to the admin, so we can see it in the admin.

```python
from django.contrib import admin

from schoolapp.models import School

@admin.register(School)
class SchoolAdmin(admin.ModelAdmin):
    pass
```

Now, you can see the model in the home-page of the Django admin.

{% include lazyload.html image_src="https://i.imgur.com/bFRs61N.png" image_alt="Django admin home page with registered model" image_title="Django admin home page with registered model" %}

You can simply create the entries in the database by using the admin dashboard directly.

Just go to the history page of the model to find what do we save related to the object. By default, we only store whether any changes were made to the object or not. Let's say, you want to save more data related to the changes. We can do it in this way.

{% include lazyload.html image_src="https://i.imgur.com/uJgWNCf.png" image_alt="Django admin history or LogEntry Page" image_title="Django admin history or LogEntry Page" %}

```python
from django.contrib import admin
from django.contrib.admin.options import get_content_type_for_model
from django.contrib.admin.models import LogEntry, ADDITION

from schoolapp.models import School


@admin.register(School)
class SchoolAdmin(admin.ModelAdmin):

    def save_model(self, request, obj, form, change):
        super().save_model(request, obj, form, change)
        if change:
            change_message = '{} - {} - {}'.format(obj.school_name, obj.address, obj.principle_name)
            LogEntry.objects.create(
                user=request.user,
                content_type=get_content_type_for_model(obj),
                object_id=obj.id,
                action_flag=2,
                change_message=change_message,
                object_repr=obj.__str__()[:200]
            )
```

We are overriding the default implementation of `save_model` for that given admin model. This will save everything in the `change_message`, which is visible in the action column.

{% include lazyload.html image_src="https://i.imgur.com/9MWWYe8.png" image_alt="Django admin change the data" image_title="Django admin change the data" %}

{% include lazyload.html image_src="https://i.imgur.com/CxPupRv.png" image_alt="Django admin history of object being saved" image_title="Django admin history of object being saved" %}

**Coming up**

## Counting the number of fields

## Permissions

## Link to Foreign key fields

## Custom ordering

## Custom Searching
