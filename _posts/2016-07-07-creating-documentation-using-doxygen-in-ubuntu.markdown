---
author: ranvirsingh1114
comments: true
date: 2016-07-07 21:45:36+00:00
layout: post
link: https://ranvirsinghprojects.wordpress.com/2016/07/08/creating-documentation-using-doxygen-in-ubuntu/
slug: creating-documentation-using-doxygen-in-ubuntu
title: Creating documentation using Doxygen in Ubuntu
wordpress_id: 223
categories:
- Six weeks training
---

Doxygen is a tool to create a documentation for your program/project written in the languages like C, C++, Java, python and so on. It reads the well formatted and special doxygen comments to create the required documentation. This documentation is very important for the new developers who want to help in the development of the project. Documentation is one of the main pillar of an open-source project.

Read [this post](http://wp.me/p7kUg1-3E) to more about the importance of  documentation in software development.

Let us discuss how to create documentation using doxygen. First of all you need to have doxygen installed on your system. For that you can type these commands in the terminal.


<blockquote>sudo apt-get update

sudo apt-get install doxygen</blockquote>


This is good for the beginning. But if you want to create the documentation using the graphical user interface then you can use this command. I will not be discussing this method so you have to figure it out yourself. I am taking this method to be fairly easy that you can figure it out yourself.


<blockquote>sudo apt-get install doxygen-gui</blockquote>


Now you can run the GUI using the command.


<blockquote>doxywizard</blockquote>


Now that's it for the GUI we are going to create the documentation using the terminal. Excited... so am I. So, let's start. For the example purpose I am going to create a simple hello world program in C++(The strategy is different for python but is similar to many other languages whose support is present).

This is what program looks like :-

    
    <code>/**
    * @file         helloworld.cc
    * @brief        helloworld
    * @detail       this is a simple hello world program using a function
    * @author       Ranvir
    * @include      string.h
    */
    #include <iostream>
    using namespace std;
    /**
    * @class   hello
    * @brief   simple brief intro
    * @detail  detailed intro
    */
    class hello{
    public:
    /**
    * @class   hello
    * @fn      helloworld
    * @brief   print helloworld on the terminal
    */
        void helloworld(){
            cout<<"hello world";
        }
    };
    int main(){
       cout<<"Hello world";
       cout<<"\n";
       hello obj1;
       obj.hello();
       return 0;
    }
    
    </code>


Is this the basic context of a C++ file. No, it contain some extra components written in the a block of comment section. These are the Doxygen comments and they are used by this tool to depict the various parts of the program. According to the official site of [Doxygen](http://doxygen.org), there are many ways to start a comment in a file. For eg:- We can do it by these ways:-



 	
  * /**      -----------          comments                   */

 	
  * ///      single line comment in Doxygen

 	
  * """ special comment block for python """

 	
  * /*!                  comment                                 */


While writing the comments we have to follow a pattern with the tags i.e. before every tag we should have something special so that Doxygen can understand what are we creating. Actually Doxygen read these tags and place them at special location in the generated output. So, we have to specify them explicitly. So the two common sign used are

 	
  1. @

 	
  2. \


We have used @ in the shown example. We can also use \ in place of @.

Now we need to generate the configuration file for the project. The configuration file contain the content in which the various variables of the Doxygen file are defined. While you are in the directory where your project is present. You can also create a separate folder for the doxygen content.For this purpose use this command.


<blockquote>$ doxygen -g filename</blockquote>


From above command filename is optional, if no filename is given a file named Doxygen is generated. Now I will assume that you have not used any file name.

Next you can edit this file and add the content according to your needs. For example you can give a name to your project using this file. For editing use this command.


<blockquote>$ vim Doxygen</blockquote>


I hope you know something about vim. If no read [this post. ](http://wp.me/p7kUg1-1Z)

Great now this is the time to generate the Documentation. Go on and type this command in the terminal.


<blockquote>$ doxygen Doxygen</blockquote>


Where Doxygen is the name of file we generated earlier. Now you will find two directories in the place where your files were present. Use these commands to see the generated html documentation.


<blockquote>$ cd html

$ firefox index.html</blockquote>


To see the latex output, Move out of this directory by using these commands.


<blockquote>$ cd ..

$ cd latex

$ make</blockquote>


Now open the pdf output. You will see the documentation in the pdf format.

Still unable to figure out. Post a comment and I will love to help.

Thanks for reading :)
