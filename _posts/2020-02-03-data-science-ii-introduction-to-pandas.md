---
layout: post
title: Data Science II - Introduction to Pandas
date: 2020-02-02T17:44:47.959Z
published: false
tags:
  - machinelearning
  - datascience
  - python
  - pandas
categories:
  - machinelearning
  - datascience
  - python
  - pandas
---
Pandas is an open source library built on the top of `NumPy` that allows us to analyse and clean the data for further step to be performed upon.

> Pandas is a fast, powerful, flexible and easy to use open source data analysis and manipulation tool, built on top of the Python programming language.

Pandas is the next step that you need to know if you are starting out as a data scientist. As it is built on the top of Numpy, that is why studied about [Numpy](https://ranvir.xyz/blog/data-science-i-all-things-you-need-to-know-about-numpy/) first.

## Pandas features

* Pandas library has a built-in visualization which you can use which we are going to discuss in the next few parts.

* It can work with a wide variety of data sources and can help us to clean them up.

There are a lot of other features which you might find useful, but this is what we need for the start.

## How to install Pandas?

Installing Pandas is quite similar to installing Numpy as we did in the last part.

When in your virtual environment, use the following command

```shell
pip install pandas
```

## What are we going to learn?

We are going to learn various methods of the Pandas library which will help us to clean and analyse the code.

Some important terms we will be seeing in this post are:

* Series
* DataFrames
* Missing Data
* GroupBy
* Merging, Joining and Concatenating
...

## Series in Pandas

{% include lazyload.html image_src="https://i.imgur.com/64xGCPE.png" image_alt="pandas series" image_title="pandas series" %}

Pandas series are similar to Numpy Array except that the pandas series should contain some indexes.

Let's jump to the Jupyter notebook to learn more about the Pandas series.

[Pandas Series Jupyter notebook](https://github.com/singh1114/ml/blob/master/datascience/Pandas/Pandas%20Series.ipynb)

### Recap

In this notebook, we discussed,

* How to create Pandas series?

* How to create Pandas series with custom indexes?

* Creating series using Python dictionaries.

* How to select elements from pandas series?

* How to apply arithmetic operations in Pandas series?

**NOTE:** When you do arithmetic operations on pandas series with `int` type, it will convert it to `float`.

## DataFrames in Pandas

{% include lazyload.html image_src="https://i.imgur.com/ZhwhESU.png" image_alt="Pandas DataFrame" image_title="Pandas DataFrame" %}

A Pandas DataFrame is a combination of Pandas series clubbed together in form of rows/ columns.

Let's jump on to the Jupyter notebook and continue the discussion over there.

[Pandas DataFrame Jupyter notebook](https://github.com/singh1114/ml/blob/master/datascience/Pandas/pandas%20dataframe.ipynb)

In this notebook, we learned about the following topics.

* How to create Pandas DataFrames?

* How to select column series from DataFrame?

* How to add new data into the Pandas DataFrame?

* How to remove series from Pandas DataFrames?

* How to select rows from Pandas DataFrames?

## DataFrame Operations

> Normal python `and` and `or` don't work because they doesn't have the capability to compare boolean values in a series.

[Numpy DataFrames Operations Notebook](https://github.com/singh1114/ml/blob/master/datascience/Pandas/Pandas%20selection%20and%20DF%20updates.ipynb)

In this notebook we learned about the different methods used in Pandas to select, manipulate and operate on Pandas DataFrames.

## Working on missing data in DataFrames


