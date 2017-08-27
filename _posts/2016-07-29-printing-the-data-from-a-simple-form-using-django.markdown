---
author: ranvirsingh1114
comments: true
date: 2016-07-29 17:26:18+00:00
layout: post
link: https://ranvirsinghprojects.wordpress.com/2016/07/29/printing-the-data-from-a-simple-form-using-django/
slug: printing-the-data-from-a-simple-form-using-django
title: Creating a custom form in Django with special options
wordpress_id: 237
categories:
- Django
- Six weeks training
---

In this post I am going to elaborate my journey of creating a html form in django and then extracting the python variables from the inserted data. After doing that we can do almost anything with this data.

We can retrieve data from the django models or we can print them out in the browser. There was a specific reason for which I wanted to do that. Actually my database was created using admin panel. There was a lot of data in the database. I just wanted to retrieve that data using the data given by the user.

The user can select the data according to the categories and I had to show that data using the given filters. So, I started the journey by using a simple form. I never knew that in Django we have to create a separate file for forms due to this, I went forward to create a simple html form in the Django templates. I spent a lot of in this and finally came to know that there existed an easier path.

**Creating a custom form in Django**

First of all you have to create a file named forms.py in the app on which you are working(Now many smart people suggest that we must create another app for different purposes in the particular web app but for the simpler process we will work on a single app). Now the content of the forms.py should be according to the form that we want to show as the output form. For example if we want to create a form with a name field and an age field then the content of forms.py will look like.



    
    <code>from django import forms
    class nameform(forms.Form):
    	name = forms.CharField()
    	age = forms.IntegerField()</code>


Now we need to need to create a view for this form. So that we can show this form.

**Creating the views of the custom form**



    
    <code>from .forms import nameform
    def nameageform(request):
    	form = nameform(request.POST or None)
    	context = {
    		"form" : form
    	}
    	return render(request, "yourapp/forms.html", context)
    </code>


Now your job is to create a template named forms.html inside yourapp/templates/yourapp/

**Creating template of your custom form**

This is the content of the file named forms.html

    
    <code>{% extends 'webportal/base.html' %}
    {% load staticfiles %}
    {% block content %}
    <h1>Form</h1>
    <form method="POST" action="output/">{% csrf_token %}
    {{ form.as_p }}
    <input type="submit" value="Create Post" name="">
    </form>
    {% endblock %}</code>


You can look your form working once you will set up the urls for the form in the urls.py file.

After this you have to create a function named output in the views.py that will render the views when the data is posted on the form.



    
    <code>def output(request):
    	query1 = request.POST.get('name')
    	return HttpResponse(query1)</code>


Now we need to do the final step i.e. to create a url of this view. The content of the file urls.py will look like this :-



    
    <code>urlpatterns = [
        url(r'^product/output/$', views.output, name="output"),
    ]</code>


Hope this post will help you to save a lot of your time. Thanks for reading and feel free to comment.
