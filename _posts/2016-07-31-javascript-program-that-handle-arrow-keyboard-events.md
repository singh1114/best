---
title: Simple JavaScript program that handle Keyboard events
date: 2016-07-31 13:31:15 Z
categories:
- JavaScript
- Six weeks training
author: ranvirsingh1114
comments: true
layout: post
link: https://ranvirsinghprojects.wordpress.com/2016/07/31/javascript-program-that-handle-arrow-keyboard-events/
wordpress_id: 244
---

In this post I am going to talk about one of important aspect in programming i.e. handling keyboard events. Now being important doesn't mean that it is difficult but I have to admit that I haven't tried it from the day I had started programming. Now I was working with one of my [friend](http://amisha2016.wordpress.com) and she wanted me to do it for her. I found the task interesting as I haven't done it earlier.

Here in this post I am not going to create a simple JavaScript program that will raise an alert whenever any of the arrow key is pressed. The program will detect the arrow key at any point while the browser is working. But before diving in we will discuss the very basics of the keyboard event handling in JavaScript.

There are three basic types of keyboard event Listener in JavaScript that handles this type of event.



 	
  1. keydown

 	
  2. keyup

 	
  3. keypress



 	
  * Keydown stands for the stage when the any key is pressed.

 	
  * Keyup is the exact opposite of keydown

 	
  * Keypress only works when one of the character key is pressed. You might like to work with this when you want to work with something fixed.


After reading this you should have got a clear view that what we want to try is keydown event.

Now lets dive right into the program and write some code.

    
    <!DOCTYPE html>
    <html>
      <head>
        <title>Nothing</title>
        
          window.addEventListener("keydown", onkeypress, false);
          function onkeypress(key){
            if(key.keyCode == "37"){
              alert("Left key is pressed");
            }
            if(key.keyCode == "38"){
              alert("Up key is pressed");
            }
            if(key.keyCode == "39"){
              alert("Right key is pressed");
            }
            if(key.keyCode == "40"){
              alert("Down key is pressed");
            }
          }
        
      </head>
      <body>
      </body>
    </html>


Now the coding part is pretty straight forward but still if you find something odd about this program please drop a comment and I will get back to you.
