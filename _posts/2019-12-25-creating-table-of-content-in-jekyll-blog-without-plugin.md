---
layout: post
title: How to Create a Table of Content in Jekyll blog | Without any Plugin
date: 2019-12-25T10:54:49.199Z
published: true
image: 'https://i.imgur.com/PXpPGSh.png'
tags:
  - jekyll
  - blogging
  - seo
categories:
  - jekyll
  - blogging
  - seo
---
Table of content is one of the best ways in which you can allow your user to skim through your article. Have you ever wanted to have a Wikipedia style table of content in the blog post? So that your users can easily navigate through the post that you have written.

![Creating table of content in Jekyll Blog](https://i.imgur.com/PXpPGSh.png "Creating table of content in Jekyll Blog")

## How will it help you to have a table of content?

Let's talk about the benefits that you can get by having a table of content.

### Improving the user experience

Having a table of content can help you with improving the user experience for your long posts and I have a good number of long posts on this blog, I wanted something like this for a long time. This can allow users to skim through your posts and allow them to read things that they care about.

### Improving the SEO of your Jekyll blog

It can also help you to improve your SEO. Most of the times the table of content is in the top half of the post. Whenever a search engine goes through the post and it finds all the relevant links to various headings at the beginning of the post, it ranks you higher than your competition.

## The strategy behind creating a table of content on a Jekyll blog

We want a table of content for a blog post. The easiest way to create a table of content is to target the headings in the post. We will go through the whole post's content and fetch all the H2s. All the H2s will have unique HTML ids, so we will be able to link to those easily. Not going below H2s because of the obvious complexity reasons here.

Few test cases that I want to cover before diving in.

* The table of the content widget should be hidden if no heading in the post.
* By default, every post should have a table of content visible.
* There should be an option on the post level, which allows me to hide this for that specific post.

## Creating a table of content widget in Jekyll blog

I searched over the internet to find a few of the open-source projects to help me with this but none of them suited my use case so I decided to build it myself. Moreover, I felt that a JavaScript solution will be an overkill considering the complexity of the problem. 😇

All I needed was to loop through the H2s and put everything into an array so that I can save everything in two variables. One storing all the heading texts and another storing the HTML IDs.

It was harder to implement then I thought, The hardest part to figure out was to split the HTML in a way so that I can get the H2 tags separated.

After a few hours of fighting with the liquid tags and a few breaks later, I was able to find the solution. 🎉

## Code to implement the table of content on Jekyll blog

Add the above code to _includes/toc.html.

Now you can include this widget wherever you want to use the following code.

If you want to skip the table of content from a certain page, all you have to do is to add skip_toc: true to the front matter of the post.

## Conclusion

I think we were able to get all of the three requirements working as well.

That's it from my side. Please share the page with your friends and let us how it looks?
