---
layout: post
title: 'Vim: The best text Editor for editing your files everywhere'
date: 2016-06-09T17:51:41.000Z
description: >-
  Vim being the best text editor around and available throughout every platform
  available out their. This post will help you to learn vim faster and make
  changes as fast as you can.
published: true
tags:
  - vim
  - text-editor
  - programming
categories:
  - Six weeks training
  - vim
  - text-editor
  - programming
---

I was introduced to `vim` by one of the senior during my college. As soon as I found about it, I fell in love with it.

I liked the thinking of not moving your hand off the keyboard so I explored more about this. I used one of the great website of tech world called [linux.com](https://www.linux.com/learn/vim-101-beginners-guide-vim) for the reference purpose.

## Install vim on your machine

I installed this on my system by using the command.

```shell
sudo apt-get install vim
```

On most of the systems you can find `vim` already installed on the machines.

You can use the following command to install vim on MAC.

```shell
brew install vim
```

So let's start with the things that I have learned about Vim.

Why would you even try to waste your time toward learning a full flagged text-editor. Vim is world's best text editor for a reason whenever you work with Vim you never have to move your hand off the keyboard.

You don't need to go to mouse again and again and waste your time during the purpose.

Your total typing speed will increase in the long run. Although their may be dip in the speed when you are trying it for the learning purpose but if you choose to start then this will the best decision that you might have made in a long time.

## Different Modes available in Vim

Many people in the tech may contradict this but in this post we will be talking about three modes in the vim. These three modes are
 	
* Command Mode
 	
* Insert Mode

* Last-Line Mode

* Visual Mode

We can check for the version of Vim by launching the command

```shell
vim -v
```

Press `:q` to quit this mode.

Whenever we open a file by placing a command

```shell
vim filename
```

where filename is the preffered name of your file, this command first checks for the  existence of the file. If the file exist then it opens it and if their is no file by this name then it create it and opens a blank file for us with ~ sign on the beginning of each line.

This sign represents the empty line in the document. Now while using this command the editor opens in the terminal only. The first mode in which the file opens is the command mode this mode is used is used move in the document i.e. you can press `j` to move the cursor one line down.( we will discuss more about the commands later.)

We can switch to the to insert mode by using `i` key. Press `i` key to open this mode. You can change anything in the document when you are in this mode.

The other mode is Last-Line mode which used for other purposes like saving the file.

You can simply use the visual mode by simply using `v` while in the command mode.

Visual Mode can help you with copy-pasting the parts of the text.

## Moving around through the text in vim

> Most of the commands are used in command mode unless specified otherwise.

Moving around the file is one of the main reason why would someone need to touch the touchpad or mouse.

Vim tries to make it fairly easy for you to move around in the long and big files.

### Jumping to a specific line number

```shell
:<line_number>
```

**Example**

```shell
:500
```

### Finding something specific in the file

```shell
/search_term
```

Once you get to one of the instance, keep typing `n` to find more instances of the same text.

### Moving around

* `j` is for going down.
* `k` is for going up.
* `l` is for going right by one character.
* `h` is for going left by one character.
* `shift + g` is for going all the way to the last line of the file.
* `$` is for going to the last character of the line.
* `0` is for going to the first character of the line.
* `w` is for jumping over the words.

## vim is slow while opening large files

Vim is a good option to edit files of any size but as the size of the file increases, it becomes really slow to load the first screen of the vim.

So, if you only want to read the file and don't really want to make any changes, you can switch to some other alternatives which doesn't load the full file in the memory and only loads the parts that are visible. ( `less` is one good alternative).

I tried to open one of the log file, with more than `20000 k` lines using `vim` and `less` commands to compare the time taken. It includes the time taken to open and close the files.

I used the [time shell command](https://www.ostechnix.com/how-to-find-the-execution-time-of-a-command-or-process-in-linux/) to compare these time differences.

### Time output while opening the file using vim

```shell
vim app-logv2.log-2020-01-23-1579792201  7.51s user 0.82s system 90% cpu 9.203 total
```

### Time output while opening the file using less

```shell
less app-logv2.log-2020-01-23-1579792201  0.03s user 0.01s system 5% cpu 0.579 total
```

Clearly the differences are huge and it is also because of the numerous plugins that I am using to power vim installation in my local system.

I hope you liked this post. Do share your experiences with vim and share your favourite tricks as well.

{% include linked_post.html url="copy-paste-vim-content-on-system-clipboard" %}

This is the basic overview of Vim. Please refer to other posts in the category.
