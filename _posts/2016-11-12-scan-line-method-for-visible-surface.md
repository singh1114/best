---
layout: post
title: Scan line method for visible surface detection | computer graphics
date: '2016-11-12T13:15:00.000-08:00'
author: Fierce Warrior
tags:
  - Visible surface detection
  - Computer science and engineering.
  - Scan line method
  - Depth buffer method for visible surface detection
  - Back face method
  - Computer graphics
modified_time: '2016-11-12T13:15:39.285-08:00'
published: true
---

It is an Image-space method for visible surface detection.

    Scan line method is also one of the method for detecting the visible surface on the screen. This method is similar to the method discussed in the polygon fill method. The only difference is that their are going to be more surfaces than earlier.

    In scan line algorithm we create two tables, first one is known as polygon table which is different for each and every polygon and the other one is known as edge table.

    The content of the polygon table constitutes of:

    *   Coefficients of the particular polygon's equation
    *   Color information of the particular polygon 
    *   A flag that is initialized to false  

    On the other hand the edge buffer consist of end points of each edge and for each edge the corresponding pointer pointing to the polygons that impacts on the given edge range. It also consist of inverse slope of each line.

    Whenever a line is being drawn a list is initiated, this list has all the polygons that can effect the formation of the line. This helps in only checking the given polygons and leaving out the rest. Flag is used to tell where the given line is inside the polygon or is outside it.

    The computations are done from left to right. At left most postion the flag is turned On and on the rightmost position, it is set to OFF.

    We are only going to look for the depths once the flag is set for more than one polygons. In the rest cases we are not going to think about it.

    In the next tutorial we are going to discuss one more visible surface detection method.
