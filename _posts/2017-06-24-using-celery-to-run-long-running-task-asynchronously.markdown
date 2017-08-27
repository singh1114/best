---
author: ranvirsingh1114
comments: true
date: 2017-06-24 18:41:18+00:00
layout: post
link: https://ranvirsinghprojects.wordpress.com/2017/06/25/using-celery-to-run-long-running-task-asynchronously/
slug: using-celery-to-run-long-running-task-asynchronously
title: Using celery to run long running task asynchronously
wordpress_id: 805
categories:
- GSoC-2017
---

The heading itself is a bit confusing. So, let's try to break it down by taking the example of what we wanted to achieve with this.

Our job was to run code scans when the user gives us an URL in the URL field. If you are reading the earlier posts, we have achieved somewhat similar results. But the problem is that the scanning is a long and tedious task and takes a lot of time. And for the time the server is generating the output, the user has to wait on the same page for a lot of time.

So what we wanted to do was that run these tasks on the server as separate operations, totally different from the simple tasks that are happening on regular basis. Only the tasks that are very simple are included in the main part.

This thing can be thought of being related to the threads. The main thread runs all the operations but on some occasions, we have some child threads that runs synchronously with the main thread. While this concept is used to reduce the execution time, we are using similar thing, celery to provide good user experience.

![](http://imgur.com/VXGTlPCl.png)

This form was created to take the URL from the user. Once the user gives in the URL, we handle the tasks in the tasks.py file, where all the stuff is defined.

Now we used a library called `celery` for running these tasks in the background. What we did was as follows:

We sent the users to a waiting URL. The same waiting URL will be used to show the results when the tasks are done and results are generated. The waiting URL will look somewhat like this:

![](http://imgur.com/im9Nufel.png)

We can also integrate the email system that will ask the user to give the email and the system will notify them when the tasks are done.

After the completion of tasks when the user reloads the page, he will get the following results. We are not looking to get proper formatting of the result for now. This is one of the upcoming task.

![](http://imgur.com/gLOyyEsl.png)

If you compare the URL of the one giving the output to wait and the URL that shows the results, you will find that both of them are same.

**So what's happening in the backend? **

Basically, I used a small trick up here. I coded the following model.

    
    <code>class CeleryScan(models.Model):
    </code> <code>    scan_id = models.AutoField(primary_key = True)
    </code> <code>    scan_results = models.CharField(max_length = 20000, null=True, blank=True)
    </code> <code>    is_complete = models.BooleanField(default = False)
    </code>
       <code>  def __str__(self):
    </code> <code>         return str(self.scan_id)</code>


The hack is to use `is_complete` attribute in the model. Whenever a user gives an URL to scan we generate an instance of the `CeleryScan` class and send it to the celery task manager. What we have to remember here is the `scan_id`. `scan_results` is initialized to `null` and `is_complete` variable is assigned to `False`.

Finally, when the tasks are done models are updated by using the same `scan_id`. We give the string output to the `scan_results` and set `is_complete` is set to True.

In `views.py`, I wrote the code that will take the `scan_id` from the URL. If the is_complete variable for the same `scan_id` is True then results are shown otherwise the same `'Please wait'` message is shown.

**How does celery works: **

Celery creates a queue of the incoming tasks. First, we register various tasks that are going to be executed by celery. Whenever such task is encountered by Django, it passes it on to celery. It also doesn't wait for the results. Each task reaching the celery is given a task_id. We can check for various things about the task using this task_id.

**How to use celery: **

I used the following sources to include celery in the project.

[https://code.tutsplus.com/tutorials/using-celery-with-django-for-background-task-processing--cms-28732](https://code.tutsplus.com/tutorials/using-celery-with-django-for-background-task-processing--cms-28732)

[http://docs.celeryproject.org/en/latest/django/first-steps-with-django.html](http://docs.celeryproject.org/en/latest/django/first-steps-with-django.html)

It's fairly simple. Please refer to the following commit for the code related to this post.

[https://github.com/nexB/scancode-server/commit/4986bec7edad61f4f182b54e594ee3f5efe3c2e8](https://github.com/nexB/scancode-server/commit/4986bec7edad61f4f182b54e594ee3f5efe3c2e8)
