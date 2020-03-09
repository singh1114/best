---
layout: post
title: PHP cheat sheet for exams
date: '2016-12-03T12:41:00.000-08:00'
author: Ranvir
tags:
- cheat sheet
- exam material
- Computer science and engineering
- for-each loop
- MYSQL
- loops
- PHP
- if-else
- switch
modified_time: '2016-12-03T12:41:07.573-08:00'
---

<div dir="ltr" style="text-align: left;" trbidi="on">

<div style="line-height: 100%; margin-bottom: 0cm;">**Php cheatsheet**</div>

<div align="left" style="line-height: 100%; margin-bottom: 0cm;"><?php</div>

<div align="left" style="line-height: 100%; margin-bottom: 0cm;">// write php code here</div>

<div align="left" style="line-height: 100%; margin-bottom: 0cm;">?></div>

<div style="line-height: 100%; margin-bottom: 0cm;">The PHP code can be embedded anywhere in the HTML document.</div>

<div style="line-height: 100%; margin-bottom: 0cm;">PHP stands for PHP: Hypertext Preprocessor.</div>

<div style="line-height: 100%; margin-bottom: 0cm;">Php is open-source and free to download and use.</div>

<div style="line-height: 100%; margin-bottom: 0cm;">PHP scripts are executed on the server and resulted markup is displayed on the browser.</div>

<div style="line-height: 100%; margin-bottom: 0cm;">PHP file must end with the extension of .php.</div>

<div style="line-height: 100%; margin-bottom: 0cm;">**Tasks of PHP**</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">It generates dynamic content.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">It can create, delete and make new files on the server.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">Form handling is one of the most important tasks of PHP.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">It can work with our database and keep stuff for further examination and use.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">It can also be used for the encryption of the data.</div>

<div style="line-height: 100%; margin-bottom: 0cm;">**The Installation process**</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">The process of PHP installation is very easy.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">First of all, we need a server, Apache is the best and freely available and fit for every task.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">Apache installation is very easy. Use any of the tutorials out their and install the server.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">After this install PHP parser, that will execute the PHP code on the server and pushes the result onto the browser.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">If someone want to make use of the data entered by the users than it is good option to use a database. MySQL will be a good option.</div>

<div style="line-height: 100%; margin-bottom: 0cm;">**Comments**</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">After so much of experience as a programmer, I have found that comments are the most important thing in the total code.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">So almost all the languages have a similar kind of comment but it is good to discuss them before looking toward the code.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">/* ... This is multiline comment */</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">// ... This a single line comment</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;"># ... This is also a single line comment</div>

<div style="line-height: 100%; margin-bottom: 0cm;">**Case sensitivity**</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">Now PHP case sensitivity is something that one should talk about. It is not like most of the programming languages that I have encountered till now.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">In PHP variables are case sensitive and rest stuff is not case sensitive.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">i.e. we can use ECHO, echo or EcHo for the printing something on the browser, but if the name of the variable is ‘myname’ than we can’t write it as something else. Now this is something awkward. I don’t know why PHP creators did this but I am sure their might be a good reason.</div>

<div style="line-height: 100%; margin-bottom: 0cm;">**PHP variables**</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">PHP variables are very easy to create.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;"><?php</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">$me = “ranvir”;</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">$you = “somename”;</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">$me_age = 21;</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">?></div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">Now I want to mention here that semicolon is very important in PHP and cause a very bad and unrecognizable error. So always keep in mind to put the semicolons.</div>

<div style="line-height: 100%; margin-bottom: 0cm;">**Rules of naming variables:**</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">Variables must start with a $ sign.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">The variables name must not start with the number.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">Underscores can be included in the beginning of the variable name.</div>

<div style="line-height: 100%; margin-bottom: 0cm;">**Printing the variable**</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">Now there are two ways of doing this.Command echo is used to print something on the browser.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;"><?php</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">echo “my name is $me”;</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">echo “my name is “ . $me;</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">?></div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">It is up to you to choose anyone of them but I prefer the second one because it provides with more clarity.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">As we know that we cannot provide the datatype of the variable before declaring it in PHP, that is why PHP is known as **“Loosely typed language”.**</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">Some other such languages are JavaScript and Python.</div>

<div style="line-height: 100%; margin-bottom: 0cm;">**Variable scopes**</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">The variable named in the starting of the PHP tags are almost global for the whole document.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">The variables that are inside a function are called a local variable.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">If we place a keyword global before any variable name then it accesses the global variable, even if the function is being executed. PHP also stores all the global variables in an array.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">Example:</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;"><?php</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">$x = 10;</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">function newFunc(){</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">global $x;</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">static $y = 20;</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">echo $x;</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">echo $GLOBALS[‘x’]; // Both will give the same result.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">}</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">echo $y; // As the variable is static it still exist.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">?></div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">Static variables are not deleted as soon as the execution of the execution of the function is ended. This is needed a sometimes one may want to use the variable further.</div>

<div style="line-height: 100%; margin-bottom: 0cm;">**Writing or Printing on the users Browser**</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">Writing on the browser can be done by using echo or print. Both are same but there is a minor difference.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">Echo doesn’t return anything while print does return 1.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">Echo is also somewhat faster than print.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">Print can be used in the expression for checking successful printing.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">Example:</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;"><?PHP</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">echo “Oh! It’s hot out their.”;</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">print “It’s okay.”;</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">print(“No it’s not”);</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">?></div>

<div style="line-height: 100%; margin-bottom: 0cm;">**Data types in PHP**</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;"><u>String:</u></div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">$me = “knowledge”;</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;"><u>Integer:</u></div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">$x = 10;</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;"><u>Float:</u></div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">Fractional numbers,</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">$x = 10.9;</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;"><u>Boolean:</u></div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">True or flase,</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">$x = true;</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;"><u>Array:</u></div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">More than one value can be stored,</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;">$x = array(‘you’, ‘it’, ‘me’);</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;"><u>Object:</u></div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;">The variable that stores the value and some additional value related to that value. This allows us to introduce the concept of classes.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><?php</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;">class Person() {</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;">// constructor that works whenever a object of this class is made.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;">function Person() {</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;">$this->name = “Knowledge”;</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;">}</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;">}</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;">// Now create a object and the constructer will work on its own.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;">$me = new Person();</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;">echo $me->name;</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;">?></div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;">We will see ‘Knowledge’ on the screen.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm;"><u>Null:</u></div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;">While creating a variable if no value is assigned to that variable by the programmer then by default the null value is assigned. Also, we can specifically keep a variable null to assign a new variable afterward.</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;">$x = NULL;</div>

<div style="line-height: 100%; margin-bottom: 0cm; text-decoration: none;">**Strings**</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;">Strings are one of the most used datatypes in any programming languages. Many string operations are very difficult to perform</div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-variant: normal;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><span style="letter-spacing: normal;"><span style="font-style: normal;">String data type has many build in functions which can be used to make our work easier. For studying s</span></span></span></span></span></span><span style="font-variant: normal;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><span style="letter-spacing: normal;"><span style="font-style: normal;">ome of these please refer to this link.</span></span></span></span></span></span></div>

<div style="font-weight: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;">[<span style="font-variant: normal;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><span style="letter-spacing: normal;"><span style="font-style: normal;">http://www.w3schools.com/php/php_ref_string.asp</span></span></span></span></span></span>](http://www.w3schools.com/php/php_ref_string.asp)</div>

<div style="border: none; margin-bottom: 0cm; orphans: 2; padding: 0cm; widows: 2;"><span style="border: none; display: inline-block; padding: 0cm;"><span style="font-variant: normal;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><span style="letter-spacing: normal;"><span style="font-style: normal;"></span></span></span></span></span></span></span></div>

<div style="border: none; margin-bottom: 0cm; orphans: 2; padding: 0cm; widows: 2;"><span style="border: none; display: inline-block; padding: 0cm;"><span style="font-variant: normal;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><span style="letter-spacing: normal;"><span style="font-style: normal;">****CONSTANTS****</span></span></span></span></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">Constants are the variables whose values never change during the execution of the program. Similarly, PHP constants are used for similar purposes.</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">define keyword is used to declare a constant.</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">Also, the CONSTANTS are global no matter where they are defined.</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">SYNTAX:</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">define(“variable_name”, “Value_of_the_variable”, “case-insensitive( true/false)”);</span></span></span></div>

> <span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><?php</span></span>

> <span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">define(“PI”, “3.14”);</span></span>

> <span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">echo PI;</span></span>

> <span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">?></span></span>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">case-insensitive is used if you want to make it case insensitive with string constants.</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">**Operators**</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><u>Arithmetic operators:</u></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; text-decoration: none; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">These include operators like additions, subtraction, multiplication etc.</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><u>Assignment operator:</u></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; text-decoration: none; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">This includes ‘=’ and ‘+=’, ‘-=’ etc. Operators.</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><u>Comparison Operators:</u></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; text-decoration: none; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">This include operators like ==, ===, <, <= and many more</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><u>Increment/Decrement operators:</u></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; text-decoration: none; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">++, -- are the two basic operators of this category.</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><u>Logical Operators:</u></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; text-decoration: none; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">and, or, not are the operators of this category.</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; text-decoration: none; widows: 2;"><span style="color: #242424;"></span></div>

<div style="border: none; margin-bottom: 0cm; orphans: 2; padding: 0cm; widows: 2;"><span style="border: none; display: inline-block; padding: 0cm;"><span style="font-variant: normal;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><span style="letter-spacing: normal;"><span style="font-style: normal;"></span></span></span></span></span></span></span></div>

<div style="border: none; margin-bottom: 0cm; orphans: 2; padding: 0cm; widows: 2;"><span style="border: none; display: inline-block; padding: 0cm;"><span style="font-variant: normal;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><span style="letter-spacing: normal;"><span style="font-style: normal;">****Conditional Statements****</span></span></span></span></span></span></span></div>

*   <div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">if</span></span></span></div>

*   <div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">if-else</span></span></span></div>

*   <div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">if-life</span></span></span></div>

*   <div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">nested if</span></span></span></div>

*   <div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">switch statements</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">These statements are all similar to the statements in any other language.</span></span></span></div>

<div style="border: none; margin-bottom: 0cm; orphans: 2; padding: 0cm; widows: 2;"><span style="border: none; display: inline-block; padding: 0cm;"><span style="font-variant: normal;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><span style="letter-spacing: normal;"><span style="font-style: normal;"></span></span></span></span></span></span></span></div>

<div style="border: none; margin-bottom: 0cm; orphans: 2; padding: 0cm; widows: 2;"><span style="border: none; display: inline-block; padding: 0cm;"><span style="font-variant: normal;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><span style="letter-spacing: normal;"><span style="font-style: normal;">****LOOPS****</span></span></span></span></span></span></span></div>

*   <div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">while</span></span></span></div>

*   <div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">do while</span></span></span></div>

*   <div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">for</span></span></span></div>

*   <div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">for each</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">All other loops are similar but for each is somewhat different.</span></span></span></div>

> <span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><?php</span></span>

> <span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$numbers = array(‘1’, ‘2’, ‘3’, ‘4’);</span></span>

> <span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">foreach($number as $value){</span></span>

> <span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">echo ‘$value + <br>’;</span></span>

> <span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">}</span></span>

> <span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">?></span></span>

> <span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">This will print all the numbers in the array with one value in a line.</span></span>

<div style="border: none; margin-bottom: 0cm; orphans: 2; padding: 0cm; widows: 2;"><span style="border: none; display: inline-block; padding: 0cm;"><span style="font-variant: normal;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><span style="letter-spacing: normal;"><span style="font-style: normal;">****Function****</span></span></span></span></span></span><span style="font-variant: normal;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><span style="letter-spacing: normal;"><span style="font-style: normal;">****s****</span></span></span></span></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">Functions are also similar to other languages.</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">SYNTAX:</span></span></span></div>

> <span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">function functioname(){</span></span>

> <span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">//…. Somestuff</span></span>

> <span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">return some_variable;</span></span>

> <span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">}</span></span>

> <span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">echo functionname();</span></span>

<div style="border: none; margin-bottom: 0cm; orphans: 2; padding: 0cm; widows: 2;"><span style="border: none; display: inline-block; padding: 0cm;"><span style="font-variant: normal;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><span style="letter-spacing: normal;"><span style="font-style: normal;">****Arrays****</span></span></span></span></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">There are three types of arrays in PHP.</span></span></span></div>

*   <div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">Indexed Array : Accessed using the numbers</span></span></span></div>

    <div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$x = array(“me”, ”they”, “we”);</span></span></span></div>

*   <div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">Associative Array : Elements are accessed using the programmer given values. These form a set of key and value pairs.</span></span></span></div>

    <div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$x = array(“me”=>”knowledge”);</span></span></span></div>

*   <div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">Multi-dimensional Array : Similar to matrices.</span></span></span></div>

> <span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">echo count($arrayname);</span></span>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">This function will print the total number of elements in an array. That’s it for now. With the provided knowledge you can easily build anything that you want. Think of something that you want to build. If you get any problem ask below.</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">**Superglobals**</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">These are the variables that are always accessible no matter what the scope is.</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">Some of these are:</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$GLOBALS:</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">As already discussed these contain all the global variables.</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$_SERVER:</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">This holds the information of header, state, paths and scripts of a server.</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$_REQUEST:</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">This is used to collect the data when a form is submitted to a particular script.</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><form method=”post” action=”<?php echo $_SERVER[‘PHP_SELF’];?>”></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">This means that the form is submitted to the script running on this page only.</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$_POST:</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">This is used to collect the posted data.</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$_GET:</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">This is used to collect data send by the method “GET”.</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">**FORMS**</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">Now we are going to talk about the handling form and doing various things with the data received.</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">A fully working example of form validation and posting.</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><!DOCTYPE html></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><html></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><body></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><script type="text/javascript"></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">// It is easy to write a comment this way.</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">// As the $_SERVER['PHP_SELF'] sends the data to the same file. It is not secure as hackers can run scripts for the particular file.</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">// htmlspecialchars will replaces the special characters into html characters.</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">// This does not allow cross-site scripting.</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"></script></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><form method="post" action="<?php echo htmlspecialchars($_SERVER["PHP_SELF"]);?>"></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">Name: <input type="text" name="name"></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><span class="error">* <?php echo $nameErr;?></span></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><br><br></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">E-mail:</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><input type="text" name="email"></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><span class="error">* <?php echo $emailErr;?></span></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><br><br></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">Website:</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><input type="text" name="website"></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><span class="error"><?php echo $websiteErr;?></span></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><br><br></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">Comment: <textarea name="comment" rows="5" cols="40"></textarea></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><br><br></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">Gender:</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><input type="radio" name="gender" value="female">Female</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><input type="radio" name="gender" value="male">Male</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><span class="error">* <?php echo $genderErr;?></span></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><br><br></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><input type="submit" name="submit" value="Submit"></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"></form></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><?php</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">// define variables and set to empty values</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$name = $email = $gender = $comment = $website = "";</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">// if the server receives some data with post request.</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">if ($_SERVER["REQUEST_METHOD"] == "POST") {</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">if (empty($_POST["name"])) {</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$nameErr = "Name is required";</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">} else {</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$name = test_input($_POST["name"]);</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">}</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">if (!preg_match("/^[a-zA-Z ]*$/",$name)) {</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$nameErr = "Only letters and white space allowed";</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">}</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">if (empty($_POST["email"])) {</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$emailErr = "Email is required";</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">} else {</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$email = test_input($_POST["email"]);</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">}</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">if (!filter_var($email, FILTER_VALIDATE_EMAIL)) {</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$emailErr = "Invalid email format";</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">}</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">if (empty($_POST["website"])) {</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$website = "";</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">} else {</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$website = test_input($_POST["website"]);</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">}</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">if (empty($_POST["comment"])) {</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$comment = "";</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">} else {</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$comment = test_input($_POST["comment"]);</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">}</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">if (empty($_POST["gender"])) {</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$genderErr = "Gender is required";</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">} else {</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$gender = test_input($_POST["gender"]);</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">}</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">}</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">// Now remove the special characters from the data received.</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">function test_input($data) {</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$data = trim($data);</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$data = stripslashes($data);</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$data = htmlspecialchars($data);</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">return $data;</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">}</span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">?></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"></body></span></span></span></div>

<div style="border: none; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; margin-bottom: 0.72cm; orphans: 2; padding: 0cm; widows: 2;"><span style="color: #242424;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"></html></span></span></span></div>

<div style="font-style: normal; font-variant: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">**PHP sessions**</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">Session variables are not stored on the user's computer that is why they are different from the cookies.</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">These are used to store the information of the user so that it can be used in multiple web pages.</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">For example, If you log in to a website on your one web page and open another web page of the same browser and found yourself still logged in. This is done with the help of Sessions.</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">Session stores the information of single user across all the web pages of a variable.</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">Session variables remain intact until and unless the browser window is not closed. Once closed the session variables are lost.</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><u>Content of file session1.php</u></span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><?php</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">// Start the session</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">session_start();</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">?></span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><!DOCTYPE html></span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><html></span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><body></span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><?php</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">// Set session variables</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$_SESSION["favcolor"] = "green";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$_SESSION["favanimal"] = "cat";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">echo "Session variables are set.";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">?></span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"></body></span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"></html></span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><u>Content of second file session2.php</u></span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><?php</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">session_start();</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">?></span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><!DOCTYPE html></span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><html></span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><body></span></span></div>

<div align="left" style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><?php</span></span></div>

<div align="left" style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">// Echo session variables that were set on previous page</span></span></div>

<div align="left" style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">echo "Favorite color is " . $_SESSION["favcolor"] . ".<br>";</span></span></div>

<div align="left" style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">echo "Favorite animal is " . $_SESSION["favanimal"] . ".";</span></span></div>

<div align="left" style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">// To print all the information about the session variables use this.</span></span></div>

<div align="left" style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">print_r($_SESSION);</span></span></div>

<div align="left" style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">// To change the session variables use this.</span></span></div>

<div align="left" style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$_SESSION["favcolor"] = "yellow";</span></span></div>

<div align="left" style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">?></span></span></div>

<div align="left" style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><?php</span></span></div>

<div align="left" style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">// For deleting session variables use this.</span></span></div>

<div align="left" style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">// remove all session variables</span></span></div>

<div align="left" style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">session_unset();</span></span></div>

<div align="left" style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">// destroy the session</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">session_destroy();</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">?></span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"></body></span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"></html></span></span></div>

<div style="font-style: normal; font-variant: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">**Attaching MySQL database**</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">MySQL is perfect for our use and can be learned very easily. Also there are many DBMS’s out there that can be used but here we are only going to discuss about MySQL.</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">Install the MySQL on your computer and we are ready to send the queries to the server.</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">Now there are two ways of connecting to the MYSQL either we can use MYSQLi or we can use PDO. PDO can make the connection with other 12 databases but Mysqli is only for Mysql.</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">The syntax of PDO is little difficult so we will concentrate on MySQLi for now.</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">Install MySQLi into the system.</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><?php</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$servername = "localhost";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$username = "username";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$password = "password";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$dbname = "myDB";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">// Create connection</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$conn = mysqli_connect($servername, $username, $password, $dbname);</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">// Check connection</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">if (!$conn) {</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">die("Connection failed: " . mysqli_connect_error());</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">}</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">// sql to create table</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$sql = "CREATE TABLE MyGuests (</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">id INT(6) UNSIGNED AUTO_INCREMENT PRIMARY KEY,</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">firstname VARCHAR(30) NOT NULL,</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">lastname VARCHAR(30) NOT NULL,</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">email VARCHAR(50),</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">reg_date TIMESTAMP</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">)";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">if (mysqli_query($conn, $sql)) {</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">echo "Table MyGuests created successfully";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">} else {</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">echo "Error creating table: " . mysqli_error($conn);</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">}</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">// Inserting data</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$sql = "INSERT INTO MyGuests (firstname, lastname, email)</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">VALUES ('John', 'Doe', 'john@example.com')";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">if (mysqli_query($conn, $sql)) {</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">echo "New record created successfully";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">} else {</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">echo "Error: " . $sql . "<br>" . mysqli_error($conn);</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">}</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">// Selecting data</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$sql = "SELECT id, firstname, lastname FROM MyGuests";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$result = mysqli_query($conn, $sql);</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">if (mysqli_num_rows($result) > 0) {</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">// output data of each row</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">while($row = mysqli_fetch_assoc($result)) {</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">echo "id: " . $row["id"]. " - Name: " . $row["firstname"]. " " . $row["lastname"]. "<br>";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">}</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">} else {</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">echo "0 results";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">}</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">// if you want to close the connection before ending of script use this.</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">mysqli_close($conn);</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">?></span></span></div>

<div style="font-style: normal; font-variant: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">**PHP and AJAX together.**</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><html></span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><head></span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><script></span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">function showHint(str) {</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">if (str.length == 0) {</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">document.getElementById("txtHint").innerHTML = "";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">return;</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">} else {</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">var xmlhttp = new XMLHttpRequest();</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">xmlhttp.onreadystatechange = function() {</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">if (this.readyState == 4 && this.status == 200) {</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">document.getElementById("txtHint").innerHTML = this.responseText;</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">}</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">};</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">xmlhttp.open("GET", "gethint.php?q=" + str, true);</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">xmlhttp.send();</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">}</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">}</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"></script></span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"></head></span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><body></span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><p><b>Start typing a name in the input field below:</b></p></span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><form></span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">First name: <input type="text" onkeyup="showHint(this.value)"></span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"></form></span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><p>Suggestions: <span id="txtHint"></span></p></span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"><?php</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">// Array with names</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Anna";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Brittany";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Cinderella";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Diana";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Eva";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Fiona";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Gunda";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Hege";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Inga";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Johanna";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Kitty";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Linda";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Nina";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Ophelia";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Petunia";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Amanda";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Raquel";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Cindy";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Doris";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Eve";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Evita";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Sunniva";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Tove";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Unni";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Violet";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Liza";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Elizabeth";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Ellen";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Wenche";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$a[] = "Vicky";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">// get the q parameter from URL</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$q = $_REQUEST["q"];</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$hint = "";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">// lookup all hints from array if $q is different from ""</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">if ($q !== "") {</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$q = strtolower($q);</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$len=strlen($q);</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">foreach($a as $name) {</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">if (stristr($q, substr($name, 0, $len))) {</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">if ($hint === "") {</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$hint = $name;</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">} else {</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">$hint .= ", $name";</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">}</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">}</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">}</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">}</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">// Output "no suggestion" if no hint was found or output correct values</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">echo $hint === "" ? "no suggestion" : $hint;</span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;">?></span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"></body></span></span></div>

<div style="font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 100%; margin-bottom: 0cm; text-decoration: none;"><span style="font-family: Liberation Serif, serif;"><span style="font-size: small;"></html></span></span></div>

</div>