---
layout: post
title: Data science I - All things you need to know about numpy
date: 2020-01-26T18:58:22.420Z
description: >-
  Numpy basics for learning data science and machine learning, with complete
  understanding of jupyter notebooks and python.
published: false
tags:
  - machinelearning
  - datascience
  - python
  - numpy
categories:
  - machinelearning
  - datascience
  - python
  - numpy
---
The first and foremost thing you need to get started in the data science and machine learning world is to have a little bit of knowledge of Python/ R.

And I already know a little bit of [Python](https://ranvir.xyz/blog/python) and have worked on it for some time in the past, I will be choosing it over R.

## What are we going to learn today?

Before you start on applying various algorithms to data to find the answers present in the data, you should be able to know the tools which you can use to apply the various operations.

The first tool which is going to help us a lot is the Numpy library.

In this tutorial, we are going to talk about the basics of NumPy library which will help us to apply all the mathematical operations to the data sets that we will receive later during the learning.

You can go forward and install the [virtual environment](https://ranvir.xyz/blog/how-to-install-django-using-virtual-environment/) along with jupyter notebook. While in the virtual environment, all you have to do is,

```shell
pip install jupyter
```

These things are pretty straight forward, so I would leave you to figure these things out on your own.

After installing jupyter notebook you can start off the jupyter notebook and rest of the installations we can directly do from the jupyter notebook itself.

You can start the jupyter notebook using the command.

```shell
jupyter notebook
```

Create a new `python3` notebook from the `new` button on the right hand side.

## Introduction to Numpy

[NumPy](https://docs.scipy.org/doc/numpy/user/whatisnumpy.html) is a Linear Algebra Library for Python. This particular library can be used to make all sorts of math related computations in python.

Also they are blazingly fast because it is executed with precompiled `C` code.

It is also important because almost all the libraries of PyData ecosystem are somehow dependent on NumPy library.

You can install NumPy using `pip`.

While in the newly created jupyter notebook, go to the first shell and use the following command.

```shell
!pip install numpy
```

You can run a jupyter notebook block using the combination of `shift + return( Enter)`.

![Installing numpy using jupyter notebook](https://i.imgur.com/iOvuHR5.png "Installing numpy using jupyter notebook")

We will mostly be using the NumPy arrays to interact with the data.

There are a few terminologies we need to be aware of before moving forward.

* Vectors: These are the 1-d arrays.
* Matrices: These are the 2-d arrays but can have 1 row or 1 column as well.

So essentially, a matrix with 1 row or 1 column can be known as a vector as well.

In general, people import Numpy as `np` to save time, you can use the same standard or prefer to stay away from it as well.

```python
import numpy as np
```

**Note:** The combination of vectors and matrices are referred as NumPy arrays. From now on we use the same analogy.

## NumPy vectors and matrices creation and library methods

Let's move to the jupyter notebook for the further discussions of numpy.

In this jupyter notebook, we are going to creating `NumPy` vectors and matrices using different methods.

We are also going to talk about different basic methods that will play an important role while performing different tasks on data sets.

[Numpy learning jupyter notebook](https://github.com/singh1114/ml/blob/master/datascience/Numpy%20array%20basics.ipynb)

## Selecting data using Numpy Array Indexing/ Positioning

All these methods are used to select specific parts and particular element from the NumPy arrays.

Let's move to the jupyter notebook and continue the tutorial up there.

In this part, we are going to learn about selecting different parts of the np arrays. Along with some basic conditional selecting, where you select certain parts using some specific conditions.

[Numpy Selection Jupyter Notebook](https://github.com/singh1114/ml/blob/master/datascience/Numpy%20index%20selection.ipynb)
