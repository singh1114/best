---
title: A word about subprocess module
date: 2017-06-21 10:17:31 Z
categories:
- GSoC-2017
author: ranvirsingh1114
comments: true
layout: post
link: https://ranvirsinghprojects.wordpress.com/2017/06/21/a-word-about-subprocess-module/
wordpress_id: 715
---

It has been a few days since I have been working on the GSoC project. Although I haven't been able to write about all the things going on that side. From now on probably I will talk about it more often. Yesterday I managed to upload the code on our local experimental server and show the results to the mentor. Thank god, it didn't break( I haven't written any code to handle the errors) and everything worked as expected. Next thing is to attach celery so that the actions happens in the background. Now both celery thing and the server are for the other day. Today I will be talking about subprocess, a module of python that we are going to use for running bash commands.

**What we have done till now:**

We have made the models which were a hectic task because we don't really know what was coming out of the scans. After that, I made two main views to start with. One for scanning URL and other for getting files from the local. Today we are going to talk about using subprocess module to run bash commands in a python program.

According to python docs, subprocess can be used as an alternative for the following purposes.

    
    os.system
    os.spawn*
    os.popen*
    popen2.*
    commands.*


We used the module for our own purpose. We used the Django to upload the file to the server using the basic FileField type in the form. Everything about that task is written in the another post which you will find under the GSoC-2017 category. After the file was uploaded we wanted to apply some bash commands for scanning the code. I was thinking of placing the scancode-toolkit code in the root directory of the project then in the bash script, we will write the following initial commands.

`$ cd ../scancode-toolkit/`

As we are in the directory inside the scancode-server. This will give us the opportunity to scan the code using the following command.

`$ ./scancode file_name`

Then the mentor said that we can directly install scancode using the following command.

`$ pip install scancode-toolkit`

This changed my view and now I was going to simply put the scancode-toolkit into the requirements.txt file. After that, I was going to import subprocess module and write a few lines of code that can scan the code.

Following is the commit in which I wrote the code to do so.

[https://github.com/nexB/scancode-server/commit/d1431724cb5241c56f3e1a7f507cf854b919af24](https://github.com/nexB/scancode-server/commit/d1431724cb5241c56f3e1a7f507cf854b919af24)

In the code, I haven't written anything to handle errors. In the next few commits, we will concentrate on doing so.

The rest part of the post will discuss some other features of the subprocess module. subprocess.call is frequently used in the case of subprocess module. A simple implementation of the subprocess is as follows:


<blockquote>`>>> import subprocess`

`>>> subprocess.call(['ls', '-l'])`</blockquote>


The result will be shown as standard output to the command line. In subprocess, we have an option to call a program by executing it like the shell does it. For that, we use the following code.


<blockquote>`>>> subprocess.call('ls -l', shell=True)`</blockquote>


For getting more information read. [http://sharats.me/the-ever-useful-and-neat-subprocess-module.html](http://sharats.me/the-ever-useful-and-neat-subprocess-module.html)

How to PIPE the result of one module to next module:

[http://kendriu.com/how-to-use-pipes-in-python-subprocesspopen-objects](http://kendriu.com/how-to-use-pipes-in-python-subprocesspopen-objects)

    
    <code><span class="n">grep</span> <span class="o">=</span> <span class="n">Popen</span><span class="p">(</span><span class="s">'grep ntp'</span><span class="o">.</span><span class="n">split</span><span class="p">(),</span> <span class="n">stdin</span><span class="o">=</span><span class="n">PIPE</span><span class="p">,</span> <span class="n">stdout</span><span class="o">=</span><span class="n">PIPE)</span>
    <span class="n">ls</span> <span class="o">=</span> <span class="n">Popen</span><span class="p">(</span><span class="s">'ls'</span><span class="o">.</span><span class="n">split</span><span class="p">(),</span> <span class="n">stdout</span><span class="o">=</span><span class="n">grep</span><span class="o">.</span><span class="n">stdin</span><span class="p">)</span>
    <span class="n">output</span> <span class="o">=</span> <span class="n">grep</span><span class="o">.</span><span class="n">communicate</span><span class="p">()[</span><span class="mi">0</span><span class="p">]</span>
    <span class="n">ls</span><span class="o">.</span><span class="n">wait</span></code><span class="p"><code>()</code> </span>


Or an alternative of communicate() is to use.

    
    <span class="gp">>>> </span><span class="n">grep</span><span class="o">.</span><span class="n">wait</span><span class="p">()</span>
    <span class="gp">>>> </span><span class="k">print</span> <span class="n">grep</span><span class="o">.</span><span class="n">stdout</span><span class="o">.</span><span class="n">read</span><span class="p">()</span>


That's it for today. We will come back with more exciting things tomorrow.
