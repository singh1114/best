---
modified_time: '2016-12-09T09:59:52.659-08:00'
layout: post
author: Fierce Warrior
title: Visible surface detection | Computer graphics
date: '2016-11-12T02:45:00.001-08:00'
updated_date: 2020-04-01T17:36:36.093Z
description: >-
  Visible surface detection basic along with a discussion on Object and Image
  space method with coherence explaination.
published: true
tags:
  - Visible surface detection
  - Computer science and engineering
  - Computer graphics
---
Hello everyone,

So today we are going to discuss one of the main topic in computer graphics i.e. Visible surface detection or some people also like to call this as hidden-surface removal. It is one of the many less understood topic. So let's dive right into the topic.

First of all, we need to understand the basic concept. Before moving forward please fix your eye on some particular object. There are two faces of any 3-D object, one of which is visible to you and the other one that is not at all visible for example at this particular moment I am typing on the screen so my computer screen is visible to me but the back side of computer is not at all visible to me.

So why are we even discussing this thing?

We are discussing this thing because this will help us to save us a lot of computational time as we are not going to think about the objects that are not included in the final display. We are not going to ask our computer to make some part on the screen which is not visible.

Definitely this will reduce the overhead on the computer for extra computation. Also these computations are not at all required in the final display. Finally, we are going to show only the visible surfaces hence the name visible surface detection.

Now as we know the problem we need to solve this problem. So there are two ways of solving this problem.

## Object-space method

This is also called `continuous domain`. In this method we compare the parts of the objects in `3-D` to each other and label some parts as visible. Those parts that are labelled as visible are going to make it into the final list while the others are not going to be computed by us saving us a lot of computation time. (we use bounding boxes)

## Image-space method

    This is a discrete type of method where we check on each and every pixel that whether the particular point is
        going to be in the final display or not. This method works on the 2-D display i.e. we are going to work on the
        image not on the object. In this type of method number of pixels on the screen is a strong limitation. 

Both are good methods but Image-space method is little slower as we go pixel by pixel on the other hand
    object-space method is not good on the quality basis.

## Coherence properties

Coherence properties helps us to reduce the computations time even more. These are some of the features of the
    computer graphics that are standardized by some great people. As we know that there are the only one difference
    between 2-D and 3-D that is depth. In 3-D we also have depth along with width and height. Some of the coherence
    properties are:



    * We are not going to compare two surfaces if they are perfectly separate. (Object Coherence)
    * When we are going to plot the next pixel we will not compute the depth again and again rather we will use a simple
    value that we keep on incrementing to earlier depth level. This will also save us a lot of computation time.(Face
    Coherence) 
    * When a object from behind of a surface becomes visible then we have to show it on the screen. (Edge coherence)
    * When an object penetrates inside another object then a line is created that must be drawn on the screen. (Implied
    edge coherence)

    There are some other type of coherences that can be included here. 

* scan line coherence

Successive lines have similar spans.

* Area coherence

The span of the adjacent group of pixels is often covered by the same visible face.

* Depth coherence 

Use difference equation to estimate depths of nearby points on the same surface.

* Frame coherence

Pictures of two successive frames of an animation sequence are quite similar (small changes in object and viewpoint).

In the next post, we are going to discuss the various Visible surface detection algorithms.