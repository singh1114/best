---
layout: post
title: HTML presentation framework reveal.js and why I am a big fan?
date: 2018-04-10T09:51:00.000Z
description: >-
  How to create beautiful HTML and JavaScript powered presentations using
  reveal.js framework and converting html presentations to PDFs using decktape.
published: true
image: 'https://i.imgur.com/ZNpqIo2.png'
tags:
  - html
  - javascript
categories:
  - html
  - javascript
redirect_from: []
---
{% include lazyload.html image_src="https://i.imgur.com/ZNpqIo2.png" image_alt="Creating presentations using HTML in reveal.js" image_title="Creating presentations using HTML in reveal.js" %}

Reveal.js is an HTML presentation framework that can help you to create awesome presentations for your talk or simple knowledge transfer session in your class.

I have created a number of presentations using reveal.js.

Here are the links:

* [https://ranvir.xyz/presentations/project1.html#/](https://ranvir.xyz/presentations/project1.html#/)
* [https://ranvir.xyz/presentations/slide2.html#/](https://ranvir.xyz/presentations/slide2.html#/)
* [https://ranvir.xyz/presentations/mathjax.html#/](https://ranvir.xyz/presentations/mathjax.html#/)
* [https://ranvir.xyz/presentations/csi.html#/](https://ranvir.xyz/presentations/csi.html#/)

## Prologue (How I came to know about reveal.js)

So, during my time at college, I had to deliver a presentation to a group of students and teachers from a special student cell regarding one of the emerging technologies of those times.

My mentor at that time suggested me to use reveal for creating the presentation. I was sceptical in the beginning but as soon as I got the grip of it, I loved it. 

I went home and thought that it would be a difficult task but in the end, I ended up doing it just in two hours.

## Setting up reveal.js

All you need to run reveal powered presentation in your local system is to have JavaScript up and running and if you are reading this post, you definitely have it running.

All you have to do is to go to reveal.js GitHub page and download the latest version of the code on the website.

[Here is the link for reveal.js GitHub repository.](https://github.com/hakimel/reveal.js/)

The downloaded file would be a zip file. If in windows, open the file simply by double-clicking it.

If in Linux use these commands in the terminal to open the file. First download the unzipper by using this command.

```bash
sudo apt-get install unzip
```

Then use this code to unzip the file by giving the name of the destination folder.

```bash
unzip file.zip -d destination_folder
```

Otherwise, if you prefer, you can `fork` the code from the [https://revealjs.com/](https://revealjs.com/). Click on the fork button or clone to repo to your local.

```shell
git clone git@github.com:hakimel/reveal.js.git
```

{% include linked_post.html url="basic-commands-in-github" %}

After unzipping, open the folder and you will find an `index.html` file inside.

## Creating presentations using reveal.js

Open this file in your text editor. Inside the body, tags delete every section.

Now create each section using the beginning and ending section tag. Each section is equivalent to one slide.

Here is the reference of one equivalent slide.

<script src="https://gist.github.com/singh1114/47444f83e62a50160d78791720c461c6.js"></script>

{% include lazyload.html image_src="https://i.imgur.com/G5fQRw4.jpg" image_alt="Creating presentations using HTML in reveal.js" image_title="Creating presentations using HTML in reveal.js" %}

You can do a lot of things using reveal.js presentation creator. You can create a style of your own if you want to.

## Epilogue (Delivering the reveal.js presentation)

So, there were somewhere around 100-200 students and teachers in the hall where I was delivering the presentation. The stage was at a good height, and I was going to show a good number of charts in my presentation.

Before jumping on to the stage, I hosted the presentation on to GitHub pages website and created a [short link](https://tinyurl.com/) using one of the services out there. Finally, I shared the link with everyone in the hall.

Everyone opened the link on their phones and were able to look at the chart more clearly.

## Generating PDFs/ Screenshots of the HTML presentations

Sometimes, people share their presentation in a PDF format with their audience so that they can get it printed and go through the presentation whenever they want.

I found this awesome HTML presentation PDF convertor, [decktape](https://github.com/astefanutti/decktape/). All you have to do is to install it locally and you will be good to go.

```bash
npm install decktape
```

Also, during the writing of this article `decktape` was not working with Node version 12 for me. Please track the [issue here](https://github.com/astefanutti/decktape/issues/201).

Apply the following command to create PDF of your presentation.

```bash
decktape reveal <path_of_reveal_presentation_file> abc.pdf
```

{% include lazyload.html image_src="https://i.imgur.com/bgs1rxZ.png" image_alt="Generated PDF for HTML presentation" image_title="Generated PDF for HTML presentation" %}

There are a lot of other options you might want to try. Also, using black background for your presentation PDF can waste a lot of ink, so you might want to change that to something else.

Please subscribe to the blog for more such updates and leave your comments if you are using something similar or you don't like something like with this post.
