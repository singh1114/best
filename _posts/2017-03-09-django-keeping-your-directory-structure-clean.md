---
layout: post
title: 'Django: Keeping your directory structure clean'
date: 2017-03-09T12:50:22.000Z
description: >-
  Best Django directory structure to handle complexity of a level of top 4s.
  Django Rest Framework uses the same strategy.
published: true
author_name: Ranvir Singh
author_username: ranvir_xyz
canonical_url: https://ranvir.xyz/blog/how-does-django-validate-passwords/
tags:
  - programming
  - django
  - python
categories:
  - programming
  - django
  - python
---

Hello there!

If you have worked with Django before, then you might know the way you organise your files is very important in making your code reusable. These days I have been trying to DRF( Django's REST Framework). Along with learning, I am trying to complete a minor project.

So, I found a great article that explained a lot about the way you should keep your files in a project that is built using Django. Here is the link if you want to read it.

[Revsys blog post on clean Django directory structure](http://www.revsys.com/blog/2014/nov/21/recommended-django-project-layout/)

In this post, I am going to discuss the discrepancies that I discovered while following the tutorial.

  * After dividing the settings into some parts, your code breaks down. For running the code again you have to make changes in two places. One at the manage.py and other at wsgi.py.

```python
os.environ.setdefault("DJANGO_SETTINGS_MODULE", "your_project_name.settings.dev")
```

After doing this, you will get rid of the empty secret code error.

  * After this, you may face the 'module not found' error. For solving this, just use a dot before the name of the module that you are importing.

```python
from .base import *
```

After this, the runserver command will work.

Thanks for reading. Do comment your views.
