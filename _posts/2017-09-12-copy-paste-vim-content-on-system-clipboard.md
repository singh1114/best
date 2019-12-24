---
title: How to copy paste vim content to system clipboard
date: 2017-09-12 00:08:37 Z
categories:
- Vim
- bash
author: Ranvir Singh
comments: true
layout: post
---

Hello folks,

Today I am going to share the solution for the problem which I was facing for a long time. I have been using Vim editor from a long time now. With Vim we can work on our things without other interruptions. In other words it is the tool for increasing the productivity of the developer. If you haven't heard about Vim. [Here]({{ site.baseurl }}/categories/#Vim) are some relevant content about Vim which you can read to get more insight of the great text editor.

### **The Problem**

This problem faced is very basic and at the same time it is very irritating. We can copy-paste stuff within Vim quite easily by using the visual mode of Vim. But when it comes to pasting some stuff from the browser or some other source, it becomes quite difficult to do that. On my local system when copying stuff from the browser and used to paste in the Vim text editor, the text either got scatter with different indentation. Being a python developer, I don't like anything which is not properly highlighted.

### **The solution**

Now that we have shared the problem, it's time to share the solution. First of all, we should know whether our code editor can simply do the things that we want it to do or not. For that apply the following command while using the vim in the escape/command mode.

```
:echo has('clipboard')
```

**If the result is 1**, then there is no need to do anything. Just apply the following command in Vim or put it into ~/.vimrc.

```
:set clipboard=unnamed
```

And use the following set of keys to paste the copied stuff to the text editor.

```
"+p
```

Press all those keys, one after the other in the _escape_ mode.

On the other hand, **if the result was 0** apply the following command to get the vim having the clipboard in the bash shell.

```
$ sudo apt-get install vim-gtk
```
Now you can confirm that you have the got the clipboard feature to the _Vim_. Just open the vim and apply the _echo_ command discussed earlier.

After this follow the same procedure which must be followed if we have received 1 as the solution.

### **The Why?**

These type of things happen with Vim as it has it's own clipboard and you cannot even share text between two different instances of terminal. To overcome this problem, this solution is devised.

[Here](https://stackoverflow.com/questions/11489428/how-to-make-vim-paste-from-and-copy-to-systems-clipboard?noredirect=1&lq=1) is the source which answered the same question. The following link gave the full insight on how to solve the problem and know why it's happening in this way.

Any question, Please feel free to contact.


