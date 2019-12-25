---
layout: post
title: How to Create a Table of Content in Jekyll blog | Without any Plugin
date: 2019-12-25T10:54:49.199Z
published: true
tags:
  - jekyll
  - blogging
  - seo
categories:
  - jekyll
  - blogging
  - seo
---
Table of content is one of the best way in which you can allow your user to skim through the your article. Have you ever wanted to have a Wikipedia style table of content in blog post? So that your users can easily navigate through the post that you have written.

## How will it help you to have table of content?

Let's talk about the benefits that you can get by having a table of content.

### Improving the user experience

Having a table of content can help you with improving the user experience for your long posts and I have a good number of long posts on this blog, I wanted something like this from a long time. This can allow users to skim through your posts and allow them to read things that they care about.

### Improving SEO of your Jekyll blog

It can also help you to improve your SEO. Most of the times the table of content is in the top half of the post. Whenever a search engine goes through the post and it finds all the relevant links to various headings in the beginning of the post, it rank you higher than your competition.

## Strategy behind creating table of content on a Jekyll blog

We want a table of content for a blog post. The easiest way to create a table of content is to target the headings in the post. We will go through the whole post's content and fetch all the `H2`s. All the `H2`s will have unique `HTML` ids, so we will be able to link to those easily. Not going below `H2`s because of the obvious complexity reasons here.

Few test cases that I want to cover before diving in.

* Table of content widget should be hidden if no heading in the post.
* By default every post should have table of content visible.
* There should be an option on post level, which allows me to hide this for that specific post.

## Creating table of content widget in Jekyll blog

I searched over the internet to find a few of the open source projects to help me with this but none of them suited my use case so I decided to build it myself. Moreover I felt that a JavaScript solution will be an overkill considering the complexity of the problem. 😇

All I needed was to loop through the `H2`s and put everything into an array, so that I can save everything in two variables. One storing all the heading texts and another storing the HTML `ID`s.

It was harder to implement then I thought, The hardest part to figure out was to split the `HTML` in a way, so that I can get the `H2` tags separated.

After a few hours of fighting with the `liquid` tags and a few breaks later, I was able to find the solution. 🎉

## Code to implement the table of content on Jekyll blog

<script src="https://gist.github.com/singh1114/ce371573bbc0ce0703ea3b9c63ea21d1.js"></script>

Add the above code to `_includes/toc.html`.

Now you can include this widget wherever you want to using the following code.

<script src="https://gist.github.com/singh1114/d3eca15e881310d46e2ea49857576914.js"></script>

If you want to skip table of content from certain page, all you have to do is to add `skip_toc: true` to the front matter of the post.

I think, we were able to get all of the three requirements working as well.

That's it from my side. Please share the page with your friends and let us how it looks?
