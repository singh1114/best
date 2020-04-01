---
modified_time: '2016-11-12T12:49:27.284-08:00'
layout: post
author: Fierce Warrior
title: Depth | Z- Buffer method for visible surface detection | Computer graphics
date: '2016-11-12T12:49:00.000-08:00'
updated_date: 2020-04-01T17:37:03.112Z
published: true
tags:
  - Visible surface detection
  - Computer science and engineering.
  - Depth buffer method for visible surface detection
  - Computer graphics
---
In this post we are going to discuss one of the most important techniques for [visible surface detection](https://ranvir.xyz/blog/algorithms-for-finding-visible/). This technique is used after the [back-facing technique](https://ranvir.xyz/blog/algorithms-for-finding-visible/#back-face-detection) is used to further reduce the computation time.

This method is related to computation of depth of various objects at each and every polygon and hence finding out which objects are going to make it into the final list of the picture.

This method makes the computation at each and every point/ pixel.

Not only the depth is calculated but also the color is calculated. The final color is calculated with the polygon that is visible at the particular pixel.

`Depth-Buffer` is the variable used to save the depth while `Frame Buffer` is the variable used to save the color.

In this algorithm we take two 2-dimensional matrix( `n * n`) in which each point is represented as `(i, j)` is represented as `ith` and `jth` pixel while on the other two-dimensional matrix it represents the position while the value represents the color.

## Algorithm

* First, set depth buffer to zero and frame buffer to background color.
* Now for each point in the `n * n` matrix we are going to calculate the depth buffer for each and every polygon. 
* The polygon having the least depth buffer at is final and shown in the result. Also, the color of that polygon is given to that frame buffer.

## Advantages

* Easy to use
* Less computation time
* Can be implemented easily even with a lot of polygons

## Disadvantages

* Lot of space is used due to saving in 2-D matrices * Can't do transparent rendering.