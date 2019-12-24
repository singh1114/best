---
title: Using requests library to grab code present at an URL
date: 2017-06-22 12:09:39 Z
categories:
- GSoC-2017
author: ranvirsingh1114
comments: true
layout: post
link: https://ranvirsinghprojects.wordpress.com/2017/06/22/using-requests-library-to-grab-code-present-at-an-url/
wordpress_id: 796
---

Finally, we were on the stage to build the main module of the project i.e. the module to get the URL's from the users and return the scan results. As the first part, we are picking whatever is present at the URL, scanning the retrieved thing and showing the results.

**The approach that I was thinking of using:**

I was thinking that first of all, we would take the URL from the user in the form. Then we will pick up the files and subfolders from the location, gather everything under one location and apply scan command on the code.

For doing this I was thinking of using `wget`and `git clone` modules for the beginning. I was thinking that for the beginning we will make the checker that will check if the files can be downloaded from the URL provided. If yes then we would had used the `wget`command and if the files were not retrieved we would be had used the `git clone.`

**Clarification by the mentor:**

My mentor said that it is of lesser use to get the files from somewhere. So he asked me to use another Python module called requests. Which as far as I know converts the code on the browser to HTML. He suggested that in the next task we will be adding some condition to get the code from GitHub and BitBucket like websites.

After some clarifications from the mentor, I started writing the code. Templates to get the URL from the user were already implemented. Now I was going to write the basic logic. So I went to file`tasks.py` and wrote the following function.

This commit has everything that I did today: https://github.com/nexB/scancode-server/commit/fb72a4129fab31131f84622427a11b1675138821

In tasks.py file, first of all, I imported the requests and os module. Then I created the function that was going to be called when the user submits the form.

Now I check which folders are already present in the directory media/URL/. I used a mechanism to give recursive file names to the incoming files. The mechanism is as follows. It put all the subdirectories of the main directory into the list. After that, it sorts the list and put the file name of the next file into a variable by adding one to the list's last element retrieved by using dir_list[-1].

When this is done, we use the requests module the HTML code present at the place and put the code into the file, if the status_code of the request is 200. After that, we call the same function that was used to scancode for the local code about which I have talked in the last few posts.

After, that I have to make the view. In the view, I took the URL from the user using the form and passed it the object of the tasks.py class.

Now somewhere in the code, you will encounter `.encode('utf-8')` . This is used to encode the text received in the utf-8 format. I know a little about these encoding formats. But this encounter helped me to dig into the world of Unicode.

[**A word about character sets:**](http://wp.me/p7kUg1-cS)

**A word about the requests module:**

This module is used to send requests to a particular URL. Just use the following command to install the requests module.


<blockquote>`$ pip install requests`</blockquote>


Now to make use of the module import the module using the following command


<blockquote>`>>> import requests`</blockquote>


Simply use the module to send requests to the given URL. Using the following code.


<blockquote>`>>> r = requests.get('https://github.com/singh1114')`</blockquote>


The variable `r` will contain things like response headers, status code, error codes and many more.


<blockquote>`>>> print(r.text)`</blockquote>


Print the response text to get the output.


<blockquote>`>>> r.status_code`</blockquote>


The correct response code is 200. There might be other codes which I am unaware of. Please read them from the official documentation of requests.


<blockquote>`>>> r = requests.get('https://api.github.com', auth=('username', 'password'))`</blockquote>


We can easily pass a dictionary to the requests module. They will be used as the parameters to the request.



There are few tasks in my mind that need to be handled. I will keep you updated in this category.
