---
title: How I created separate category pages in my Jekyll blog
date: 2018-12-04 18:11:00 Z
categories:
- blogging
- jekyll
- seo
tags:
- blogging
- jekyll
- seo
---

One of the few reasons our blog takes very little time to load is because it is a static blog. [A static blog](https://weblog.masukomi.org/2015/10/18/static-vs-dynamic-blogging/) means there is no interaction with the database or any other thing which takes time to load.

I use a pretty simple stack for delivering these simple pages to your computer or phone screen. Let's dive into the process in which I created this blog.

This blog is hosted by GitHub Pages and built using Jekyll. I took the domain name from GoDaddy a few days back.

## The Problem

It's fairly easy to define categories in a Jekyll blog post. We have to write category/ categories in the frontmatter of the post. This is the front matter of the post that you are reading.

```markdown
---
layout: post
comments: true
title: "How to create separate category pages in Jekyll Blog"
subtitle: "Allow users to discover your blog more"
date: 2019-05-06 23:55:13 -0400
background: '/img/posts/books.jpg'
category: blogging
---
```

Sweet, right.

But if you go to the home page, you will find that I have found some very appealing topics about which I write regularly.

For each of them, I have created a separate page. So, the idea was that whenever I create a new post in any given category, it will add the post to the category page automatically.

I wanted the process to be as easy as possible. I found that Jekyll currently doesn't provide any pluggable way of doing this. So, I went forward with the following approach.

I created a simple HTML file in the `_layouts` directory called `category.html`. The following was the content of the file.

<script src="https://gist.github.com/jeklog/8ed69044fbc552431feb94a0ccac9acb.js"></script>

I hope you are getting what I am trying to do. I am trying to create a custom layout, which can then be directly used to create category pages.

All other code is used to display page stuff. The Real thing starts with `Line 29`. Here I create a header of the `category_name`, which will be passed when I create a category page.

Then on `Line 31`, I am only getting the posts with the same category name.

Finally, if I didn't find any post, then I will display some content.

Now I will create separate category pages.

I try to write as much clean code as possible. For that reason, I created a directory that will contain all the category pages.

So, if you want Jekyll to discover files in the new directories, you have to add the following content to <kbd>_config.yml</kbd>.

`include: ['_categories']`

Finally, you can create the category pages. Let's see the content of the Technology page.

```markdown
---
layout: category
title: Technology
description: For automating the boring tasks.
background: '/img/posts/printer.jpg'
permalink: /technology/
category_name: Technology
---
```

So only thing that you have to write is the frontmatter of the file and you are done. You can create as many separate categories as you want to.

Now whenever you write a new post, you will not have to add it to a page. Your posts will automatically be present at all the places according to the `category_name`

Just don't miss the `category_name`.

Hope you liked the way I tackled the problem. Please share your views as well.