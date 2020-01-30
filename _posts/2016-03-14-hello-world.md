---
layout: post
title: Hello World
date: '2016-12-04 18:11:00 +0000'
published: true
tags:
  - seo
categories:
  - seo
---

Hello world,

This is a website where you will find different projects for different coding languages. Keep checking the website for more details.

{% include linked_post.html url="how-to-contribute-to-open-source-and-land-a-better-job" %}

## Later

## Now

## Yesterday

## Next Month

![Creating table of content in Jekyll Blog](https://i.imgur.com/PXpPGSh.png "Creating table of content in Jekyll Blog")

{% assign images = page.media | where: "media_type", "image" %}
{% for image in images %}
  <h1>{{ image.alt }}</h1>
{% endfor %}
