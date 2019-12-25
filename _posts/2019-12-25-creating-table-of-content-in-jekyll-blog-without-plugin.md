---
layout: post
title: How to Create a Table of Content in Jekyll blog | Without any Plugin
date: 2019-12-25T10:54:49.199Z
published: false
tags:
  - jekyll
  - blogging
  - seo
categories:
  - jekyll
  - blogging
  - seo
---
Table of content is one of the best way in which you can allow your user to skim through the article. Have you ever wanted to have a Wikipedia style table of content in blog post. So that your users can easily navigate through the post that you have written.

## How will it help you to have table of content?

Let's talk about the benefits that you can get by having a table of content.

### Improving the user experience

Having a table of content can help you with improving the user experience for your long posts and I have a good number of long posts on this blog, I wanted something like this from a long time. This can allow users to skim through your posts and allow them to read things that they care about.

### Improving SEO of your Jekyll blog

It can also help you to improve your SEO. Most of the times the table of content is in the top half of the post. Whenever a search engine goes through the post and it finds all the relevant links to various headings in the beginning of the post, it rank you higher than your competition.

## Strategy behind creating table of content on a Jekyll blog

We want a table of content for a blog post. The easiest way to create a table of content is to target the headings in the post. We will go through the whole post's content and fetch all the `H2`s and `H3`s. All the `H2`s and `H3`s will have unique `HTML` ids, so we will be able to link to those easily. Not going below `H3`s because of the obvious reasons here.

Few test cases that I want to cover before diving in.

* Table of content widget should be hidden if no heading in the post.
* By default every post should have table of content visible.
* There should be an option on post level, which allows me to hide this for that specific post.

## Creating table of content widget in Jekyll blog

