---
author: ranvirsingh1114
comments: true
date: 2017-06-21 11:17:22+00:00
layout: post
link: https://ranvirsinghprojects.wordpress.com/2017/06/21/filefield-in-forms-to-upload-files-to-the-server/
slug: filefield-in-forms-to-upload-files-to-the-server
title: FileField in forms to upload files to the server
wordpress_id: 794
categories:
- GSoC-2017
---

Hello there,

In this post, I will be discussing the process that we used to process and upload files to the server.

Django provides an alternative field named FileField that allow us to add files in the forms. Before doing anything we need to add something to our settings.py file.


<blockquote>`MEDIA_URL = '/media/'`

`MEDIA_ROOT = os.path.join(BASE_DIR, 'media')`</blockquote>


These are used to create a special URL for the media files. It is useful when we are going to upload images because in this way we can attach an URL with the images. It can have various uses in the case of files.

After this, we are going to create a form in forms.py file and attach FileField to it.


<blockquote>`class LocalScanForm(forms.Form):`

`    upload_from_local = forms.FileField(label='Upload from Local')`</blockquote>


After this, we need to create a template for this.

    
    {% extends 'scanapp/base.html' %}
    {% load staticfiles %}
    {% block content %}
        <form action="" method="post">
            {% csrf_token %}
            {{ form }}
            <input type="submit" value="Submit" />
        </form>
    {% endblock %}


Create views and attach the URL to that. Here is the commit: [https://github.com/nexB/scancode-server/commit/a60cbbbb4d96d46df1232b96f7ff871e5f0e318d](https://github.com/nexB/scancode-server/commit/a60cbbbb4d96d46df1232b96f7ff871e5f0e318d)

After that, we wrote the code to handle the files. We used the subprocess module to handle the stuff. The post about that is written [here.](http://wp.me/p7kUg1-bx)

Now we are trapped on downloading stuff from an URL. We will write some code and push stuff on this blog. Till then stay tuned.
