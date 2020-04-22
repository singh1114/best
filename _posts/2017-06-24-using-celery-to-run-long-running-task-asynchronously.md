---
wordpress_id: 805
layout: post
author: ranvirsingh1114
title: Using celery to run long running task asynchronously
date: 2017-06-24T18:41:00.000Z
updated_date: 2020-04-22T16:53:44.753Z
published: true
comments: true
tags:
  - celery
  - python
  - django
link: https://ranvirsinghprojects.wordpress.com/2017/06/25/using-celery-to-run-long-running-task-asynchronously/
categories:
  - GSoC-2017
  - celery
  - python
  - django
---

Celery is used to run some special part of code which you don't want to run in the main thread. We use celery when we don't want the response of the task in the same request.

Sending notifications for the purchase could be once of the example for such a task.

## Background: What are we trying to solve?

Our job was to run code scans when the user gives us a URL in the URL field. If you are reading the [earlier posts](https://ranvir.xyz/blog/categories/#GSoC-2017), we have achieved the result and gave back the output of the request in the same response itself. But the problem is that the scanning is a long and tedious task and takes a lot of time. And for the time the server is generating the output, the user has to wait on the same page for a lot of time.

So what we wanted to do was that run these tasks on the server as separate operations, totally different from the simple tasks that are happening on a regular basis. The job of the main thread was to accept the request and send some pre-defined response.

This thing can be thought of being related to the threads. The main thread runs all the operations but on some occasions, we have some child threads that run synchronously with the main thread. While this concept is used to reduce the execution time, we are using a similar thing, **celery** to provide a good user experience.

## The solution: How did we implement it?

![](http://imgur.com/VXGTlPCl.png)

This form was created to take the URL from the user. Once the user gives in the URL, we handle the tasks in the `tasks.py` file, where all the stuff is defined.

Now we used a library called `celery` for running these tasks in the background. What we did was as follows:

We sent the users to a waiting URL. The same waiting URL will be used to show the results when the tasks are done and results are generated. The waiting URL will look somewhat like this:

![](http://imgur.com/im9Nufel.png)

We can also integrate the email system that will ask the user to give the email and the system will notify them when the tasks are done.

After the completion of tasks when the user reloads the page, he will get the following results. We are not looking to get proper formatting of the result for now. This is one of the upcoming tasks.

![](http://imgur.com/gLOyyEsl.png)

If you compare the URL of the one giving the output to wait and the URL that shows the results, you will find that both of them are the same.

## So what's happening in the backend?

Basically, I used a small trick up here. I coded the following model.

    
```python
class CeleryScan(models.Model):
    scan_id = models.AutoField(primary_key = True)
    scan_results = models.CharField(max_length = 20000, null=True, blank=True)
    is_complete = models.BooleanField(default = False)
    
    def __str__(self):
        return str(self.scan_id)
```


The hack is to use the `is_complete` attribute in the model. Whenever a user gives a URL to scan we generate an instance of the `CeleryScan` class and send it to the celery task manager. What we have to remember here is the `scan_id`. `scan_results` is initialized to `null` and the `is_complete` variable is assigned to `False`.

### Update

We can also use the `Tasks` tables provided by celery to find if the given task was completed or not.

Finally, when the tasks are done models are updated by using the same `scan_id`. We give the string output to the `scan_results` and set `is_complete` is set to True.

In `views.py`, I wrote the code that will take the `scan_id` from the URL. If the is_complete variable for the same `scan_id` is True then results are shown otherwise the same `'Please wait'` message is shown.

## How does celery works?

Celery creates a queue of the incoming tasks. First, we register various tasks that are going to be executed by celery. Whenever such a task is encountered by Django, it passes it on to celery. It also doesn't wait for the results. Each task reaching the celery is given a task_id. We can check for various things about the task using this `task_id`.

Celery works in the producer-broker-consumer format.

Our code act as a producer which sends the request to celery to save a message in the queue.

You can use any of the queue handlers out there. RabbitMQ is one of my favorites. RabbitMQ acts as a broker and saves the messages sent to it using the producer. Finally, it sends the message to the consumers.

## How to use celery?

I used the following sources to include celery in the project.

[https://code.tutsplus.com/tutorials/using-celery-with-django-for-background-task-processing--cms-28732](https://code.tutsplus.com/tutorials/using-celery-with-django-for-background-task-processing--cms-28732)

[http://docs.celeryproject.org/en/latest/django/first-steps-with-django.html](http://docs.celeryproject.org/en/latest/django/first-steps-with-django.html)

It's fairly simple. Please refer to the following commit for the code related to this post.

[https://github.com/nexB/scancode-server/commit/4986bec7edad61f4f182b54e594ee3f5efe3c2e8](https://github.com/nexB/scancode-server/commit/4986bec7edad61f4f182b54e594ee3f5efe3c2e8)
