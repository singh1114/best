---
wordpress_id: 306
layout: post
author: ranvirsingh1114
title: 'PHP : The Basics'
date: 2016-10-26T20:36:34.000Z
published: true
comments: true
link: 'https://ranvirsinghprojects.wordpress.com/2016/10/27/php-the-basics/'
---

**What is PHP?**

php stands for Hypertext Preprocessor. We have posted a lot about the python web development framework Django. It is somewhat similar to Django. PHP is the most widely used language for the server. It is used for handling the server. It is also used to interact with your database so that you can save the data for future use. PHP is also open source and free to use. PHP is very easy to learn that is why many developers believe that every new developer ;learn this as the first language.

**Installation**

Installation of PHP is very simple and can be done easily. Just go to this link( [http://php.net](http://php.net)).

**Usage**

You have to insert starting and ending PHP tags in the html where ever you want to run some PHP script. Whenever you want to run some php code save the file with the .php extension. For eg:- save this file as new.php and run using the server.

STARTING TAG : <?php

ENDING TAG : ?>

**Variables**

Variables are the most important thing that any language must have. Variables in PHP are assigned without specifying the type of the variable.


```php
<?php

$age = 20;

$name = 'Ranvir Singh';
```


This will assign $x as the value of 10. For printing you can use both echo or print. Both of them have very small difference. echo function does not return anything while print does return 1. For this reason echo is faster than print.


```php
echo $name;
```


This will print out the `Ranvir Singh` on the browser.

**String handling funtions **

String data type has many build in functions which can be used to make our work easier. For studying such functions see [this post.](http://www.w3schools.com/php/php_string.asp)

**CONSTANTS**

Constants are the variables whoes values never change during the execution of the program. Similarly PHP constants are used for similar purposes. define keyword is used to declare a constant.

SYNTAX:

define("variable_name", "Value_of_the_variable", "case-insensitive( true/false)");


<blockquote><?php

define("PI", "3.14");

echo PI;

?></blockquote>


case-insensitive is used if you want to make it case insensitive.

**Conditional statements**



	
  * if

	
  * if-else

	
  * if-elif

	
  * nested if

	
  * switch statements


These statements are all similar to the statements in any other language.

**LOOPS**



	
  * while

	
  * do while

	
  * for

	
  * for each


All other loops are similar but foreach is somewhat different.


<blockquote><?php

$numbers = array('1', '2', '3', '4');

foreach($number as $value){

echo '$value + <br>';

}

?></blockquote>


**Function**

Functions are also similar to other languages.

SYNTAX:


<blockquote>function functioname(){

//.... Somestuff

return some_variable;

}

echo functionname();</blockquote>


**Arrays**

There are three types of arrays in PHP.



	
  * Indexed Array : Accessed using the numbers

	
  * Associative Array : Elements are accessed using the programmer given values

	
  * Multi-dimensional Array : Similar to matrices.




<blockquote>echo count($arrayname);</blockquote>


This function will print the total number of elements in an array. That's it for now. With the provided knowledge you can easily build anything that you want. Think of something that you want to build. If you get any problem ask below.
