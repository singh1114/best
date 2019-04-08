---
author: ranvirsingh1114
comments: true
date: 2017-02-12 16:20:20+00:00
layout: post
link: https://ranvirsinghprojects.wordpress.com/2017/02/12/automating-the-action-of-creating-the-presentations/
slug: automating-the-action-of-creating-the-presentations
title: Automating the action of creating the presentations
wordpress_id: 625
categories:
- python
---

GitHub repository : [https://github.com/singh1114/automatingPresentations/](https://github.com/singh1114/automatingPresentations/)

8th February 2017

I came back from my so-called holidays and sir were ready to excite me with a new task on the table. As we know that the progress in the chatting app is really slow, that is why I decided to work on this side project. So the basic aim of the project is to create the presentations that are good enough to get the work done. We didn't want to create something extraordinary. The basic aim of the project is to create a markdown presentation from a Powerpoint presentation. Sir were able to get whole of the text out from the presentation and now the job is to create something is good enough with the formatting.

The file that contains the whole of the text, differentiate each slide with some references in the end. So differentiating two different slides will be easy. Next task will be to figure out what tags to be used for all the content. I saw that all the heading were written in the capitals. But we cannot differentiate between different levels of headings. So this might be done manually.

9th February 2017

Now was the time to think something about the procedure that we were going to follow. I wrote some of the pseudo code to start with.

    
    Read the file:
    
      whenever the line starts with *:
    
        read each character:
    
          if the letters are capital:
            give heading h1
    
          if the * is first in the group:
            raise the height by 50%
    
          if there is nothing after *
            do nothing
    
      if the line starts with References:
        write the code for new slides
    
    


We decided to use python for completing the job. So let the work begin.

10th February 2017

I wrote the code for the above-written pseudo code. In the end, the code written was somewhat different from the pseudo code. While writing the code I learned a few things about the file handling in python which I want to share in a quick fashion. First of all, the file handling in python does not require any type of library to be imported.

For opening a file, we can use the function open(). The parameter that we pass are:



 	
  1. The file name

 	
  2. The mode in which we want to open the file


If you know about the file handling in C, then you must know about these modes like "r", "w", "a" which stands for read, write and append respectively. The first two words are self-explanatory on the other hand append is used to append the new text to the end of the file.

read() function is used to read the content of the file and write() function is used to write some content to the file. seek() function is used to send position of the file to some other position or check the position of the pointer of reading and writing the text. Do keep in mind to close() the opened file in the end.

Now talking about the script, I used a temporary variable to check for all types of cases but still two cases are not under the hood (There might be more but for now we only know about two of them). They are as follows:

 	
  1. Even if the first word is in upper case it takes it a header text

 	
  2. Paragraphs are not handled properly.


The commit for the code is[ here.](https://github.com/singh1114/automatingPresentations/commit/956bf66deacb17fe23eb9393139464d0b23ff0f3)

In the end I wrote some documentation about the way in which this code will be used.

The commit for the documentation is [here.](https://github.com/singh1114/automatingPresentations/commit/312ab6061df88453171b0ed618cded016ef0b7bf)

11th February 2017

We were able to resolve the earlier discussed issues. Further information will be shared in some other follow ups.

Please comment on the post if there is some confusion.
