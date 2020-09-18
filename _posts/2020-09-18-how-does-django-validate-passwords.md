---
layout: post
title: How does Django validate passwords
date: 2020-09-18T19:52:26.288Z
updated_date: 2020-09-18T19:52:26.305Z
description: Django default password validation on the User model with
  createsuperuser and changepassword commands.
published: true
show_ads: false
show_telegram_signup: false
---
A few days ago, I was working with one of my old Django projects. It was running an old version of Django and I wanted to keep it updated with the latest changes that we have with the framework.

First thing first, I tried to create the superuser after creating the local database.

```python
python manage.py createsuperuser
```

When I passed in a password similar to the username it failed saying, `The password is too similar to the username.`

{{image}}

This error triggered me to find how was this working.

The first thing that I looked into was the `manage.py` file itself which in turn was importing and executing a method called, `execute_from_command_line`.

I traced it back and found a package `django.contrib.auth.management.commands`. This directory had two files.

```python
1. createsuperuser.py
2. changepassword.py
```
## The changepassword command

Since I had never used or heard `changepassword` command. I thought of trying it first and to my great pleasure, it worked. You have to pass the username as the first argument.

```python
python manage.py changepassword username
```

{{image}}

Sometimes you find gold when you read the code, right? 😍

Now let's get back to the business and look into the `createsuperuser` command class in more detail.

## Fetching the correct database

If you have been using Django for some time, you would know that Django allows you to change a lot of things depending upon the settings you define.

This also includes using some random model as your Base User model. This is the first thing that the superuser creation `__init__` constructor method checks for.

## Creating the superuser without interaction

You can use a version of the command that allows you to create the superuser without any interaction.

```python
python manage.py createsuperuser --username ranvir --email abc@abc.com --no-input
```

{{image}}

Although the user created using this process will have no password. We can create the password either using the `changepassword` command or the admin panel.

## Required fields and interactive mode

For the default `User` model, `email` is the only required field but you can change that by changing your `REQUIRED_FIELD` setting as well.

In the interactive mode( which is the default mode as well), the first thing that the prompt asks you to fill, is the username.

Django tries to smartly suggest you the current system username as the default username. (Just Wow)

{{image}}

It won't suggest the system username if it is already taken. (That's AI for me 😂)

{{image}}

After the username, you have to fill in the required field which is the email field for the default User model.

Finally, you have to fill in the password field.

## The validate password method

Sorry for keeping you waiting this long before jumping onto the real reason behind the post.

The `validatepassword` is the function that is used to validate the password provided by the user.

Again, we can configure all these validators as well, if these different password validation doesn't work for you, go forward and remove the classes from your settings file.

These are the default validators.

```python
AUTH_PASSWORD_VALIDATORS = [
    {
        'NAME': 'django.contrib.auth.password_validation.UserAttributeSimilarityValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.MinimumLengthValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.CommonPasswordValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.NumericPasswordValidator',
    },
]
```
If we use the default validators, then the password,

1. Should not be similar to `username`, `first_name`, `last_name` and `email`. It also checks for the similarity using [SequenceMatcher](https://docs.python.org/2.4/lib/sequence-matcher.html). It should be less than 0.7 similar which you can customize. (Told you, it's AI)
2. Should be greater than 8 characters.
3. Should not be in the list of common passwords. The list of common passwords is in the file, `common-passwords.txt.gz`. It contains a list of around 20000 common passwords which you should not use.
4. Should not contain all numeric characters.

I would suggest keeping the basic configuration intact for the password handling. You can use your own validations on top of it as well.

So, that's it for this time. Till next time.