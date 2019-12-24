---
title: 'Data structure: stack'
date: 2017-01-05 17:34:47 Z
categories:
- data structures
author: ranvirsingh1114
comments: true
layout: post
link: https://ranvirsinghprojects.wordpress.com/2017/01/05/data-structure-stack/
wordpress_id: 523
---

Welcome back guys,

It had been a long time since I have talked about something new. Even in this post, we are going to talk about something that we already know about. As the title of the post suggests that we will be talking about the data structure stack. We already know many things about the stack. We know how it works, we know some more things too. But we will talk about the stack in detail. In the end, we will also discuss an example that will tell us how to create a stack using our favorite language c++.

The basic function of the stack is that it works like a pile of the notebooks. In the pile, you can only take the notebooks from one side that is from the top. Similarly, in the case of the stack, we can insert as well as delete from one side only.

A variable top is used to keep the track of the total elements in the stack. When an element is added to the stack, then the top variable is incremented. On the other hand, when an element is removed then the top variable is decremented.

The process of adding an element is known as the push operation and the process of removing an element is known as the pop operation.

Now let's see the code of the implementation of the stack. Also, I want to convey that there is a way of using the stack in c++. This is the very basic implementation of the stack.

    
    #include <iostream>
    using namespace std;
    int top = -1;
    
    /*
     The push function has three parameters
     First is the stack,
     second is the element that is needed to be added.
     third is the size of the stack.
    */
    void push(int stack[], int x, int n) {
     if(top == n-1){
     cout<<"\nOverflow... There is no space in the stack";
     }
     else{
     top++;
     stack[top] = x; 
     }
    } 
    
    void pop(){
     if(top == -1){
     cout<<"\nnothing to delete";
     }
     else{
     top--;
     }
    }
    
    /*
     This function prints the size of the stack at a particular point
    */
    void size() {
     cout<<"\nSize of the stack is : "<<top+1;
    }
    
    
    /*
     Now implement these functions in the main function.
    */
    int main(){
     int stack[3];
     push(stack, 5, 3);
    
     size();
    
     push(stack, 4, 3);
     push(stack, -10, 3);
     for(int i=0; i<3;i++){
     cout<<"\n"<<stack[i];
     }
    
     // This will produce overflow
     push(stack, 10, 3);
     size();
    
     for(int i=0;i<3;i++){
     pop();
     }
     size();
     return 0;
    }


``
That's it for this post on the stack. For learning more about the stacks go to this tutorial.

[http://www.cplusplus.com/reference/stack/stack/?kw=stack](http://www.cplusplus.com/reference/stack/stack/?kw=stack)
