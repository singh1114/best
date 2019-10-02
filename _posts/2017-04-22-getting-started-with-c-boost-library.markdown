---
title: Getting started with C++ boost library
date: 2017-04-22 20:33:42 Z
categories:
- c++
author: ranvirsingh1114
comments: true
layout: post
link: https://ranvirsinghprojects.wordpress.com/2017/04/23/getting-started-with-c-boost-library/
wordpress_id: 646
---

Last few days were well spent with the C++ library boost. It was a great learning experience. I was introduced to the one of best-kept code and some new coding paradigms. Along with that it was the first time I was coding with the new standards of C++11 and C++14.

During the time I learned a lot of things which I would like to discuss in this post. I also want to share the link of GitHub that everyone can follow for the code that I will talk about in a moment.

Here is the link: [https://github.com/singh1114/parser/](https://github.com/singh1114/parser/)

As this is the first of the long lasting series about C++ I want to keep it as simple as I can. I will be discussing the various problem that one faces during his/her journey of the boost library. I would discuss this by using boost::spirit for an example.

Prerequisites:



 	
  * C++. Of course, one must know some procedural level C++. If the reader has some knowledge about polymorphism using standard template library, that would be a +1.

 	
  * This tutorial is only for the Linux user with a good knowledge of using compiling commands on the terminal.


So let's start:

**Installation:**

    
    <code><span class="pln">$ sudo apt</span><span class="pun">-</span><span class="pln">get install libboost</span><span class="pun">-</span><span class="pln">all</span><span class="pun">-</span><span class="pln">dev</span></code>


Use the above command in the terminal. This will install boost library. Find the boost library by using the locate command by using the command locate.

    
    $ locate boost


This will tell you where the boost library is located which is further going to be used while applying the command to compile.

For me, the boost library was present at:

    
    /usr/include/boost/




Now grab any code from the GitHub, using the following procedure:

First of all fork the git repo, then copy the new link produced in the URL bar, Then apply this command in the terminal.

    
    $ git clone https://github.com/your_gh_username/parser/


After this, you need to try the simplest parser which is the simple calculator. For more information about basic calculator read the readme file in the simple_calcuator directory.

Use the following commands for this purpose.

    
    $ cd parser



    
    $ cd simple_calculator



    
    $ g++ -I /path/to/boost/ -std=c++11 ascii_char.cpp -o example


Now execute the compiled file:

    
    $ ./example


g++ is the originated from GCC which stands for GNU compiler collection. This is the compiler which is used to convert C++ code to machine code and create the output in the file which is named after the file given as a parameter with -o flag. -I flag stands for includes and it includes the file which is passed as a parameter. After that, we are telling that we are going to use the standard of C++11. If we don't use -std flag then the file won't be compiled as we are using some code that was recently added to the compilers.

The next flag describes the name of the file that needs to be compiled and so on.

On execution, you can give any input as a string to add, subtract, divide and multiply.

    
    2-2 //This is a valid option


This will compute the result to 0. The parser doesn't seem to be doing much but this is the start. As they say,


<blockquote>Every big thing start with something small.</blockquote>


Now I would like to take off. If you have some doubt about the code or anything related to the post, feel free to drop a comment.
