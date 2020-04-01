---
modified_time: '2017-12-09T09:58:55.642-08:00'
layout: post
author: Fierce Warrior
title: Visible surface detection algorithms | Computer graphics
date: '2016-11-12T09:19:00.000-08:00'
updated_date: 2020-04-01T17:37:12.427Z
description: Visible surface detection basics and back-face detection algorithm basics.
published: true
tags:
  - Visible surface detection
  - Computer science and engineering.
  - Back face method
  - Computer graphics
categories:
  - computergraphics
---
There are many techniques that are used to detect various surfaces that will make to the final picture. These techniques either belong to one of the two categories that we have discussed earlier that are: Object-space method or Image-space method.

Various algorithms for visible surface detection are:

* Back-Face detection
* Depth/z- buffer method
* Scan line method
* Depth sorting method
* Area-subdivision method
* Octree method
* A-buffer method
* BSP method
* Ray casting method

In all these algorithms we are going to sort the polygons depending upon their distance from the viewport( the viewer screen). The screen that are on the top-level are going to be visible but the surfaces on the backside are not going to make to the final list. This is done by comparing the depths of the various polygons.

Let's discuss these algorithms one by one.

## Back-Face detection:

This is the type of Object-space method.

In `Back face` detection method we compute the back face of the polygon and never draw this Back face in the picture saving at least 50% of the computation time. In this algorithm we calculate this thing on the basis of dot product.

We know that if two things have a dot product between direction vector and position vector of an object greater than zero than the face is inclined toward the camera or our eye. Similarly, if the dot product is less than zero than it is a back face hence is not included in the final picture.

For example: If we take an object on the window (real world object) with a position vector

`Ai + Bi + Ci`

And we are watching the object directly parallel from the Z-axis then, The direction vector is equal to `A(0, 0, Vz)`.

Now if we calculate the dot product of this, it comes out to be.

`dot_product = Vz.C`

And if we take unit normal vector then the result is reduced to

`dot_product = C`

Now in the end we only need to have the sign of the variable dot_product, if it turns out to be positive then it is back face and on the other hand if it comes out to be negative then it is front face.

## Drawbacks:

* Partially visible surfaces cannot be computed properly as all the polygons lying over one another will have a positive dot product, but they not be visible finally but still we need to calculate them as the dot product comes out to be positive. In the final result they will be overlapped.

* Not good for advance methods like ray tracing.

* In the next tutorial we are going to discuss the next methods.