---
layout: post
title: Introduction to KNN | K-nearest neighbour algorithm using Examples
date: 2020-03-21T22:14:11.038Z
updated_date: ''
published: false
tags:
  - python
  - sklearn
  - knn
  - machinelearning
categories:
  - python
  - sklearn
  - knn
  - machinelearning
canonical_url: ''
include_mathjax: true
---
`KNN` also known as K-nearest neighbour is a [supervised and pattern classification learning algorithm](https://ranvir.xyz/blog/how-to-evaluate-your-machine-learning-model-like-a-pro-metrics/#supervised-learning-and-classification-problems) which helps us find which class the new input(test value) belongs to when `k` nearest neighbours are chosen and distance is calculated between them.

> It attempts to estimate the conditional distribution of `Y` given `X`, and classify a given observation(test value) to the class with highest estimated probability.

It first identifies the `k` points in the training data that are closest to the `test value` and calculates the distance between all those categories. The test value will belong to the category whose distance is the least.

{% include lazyload.html image_src="https://i.imgur.com/XXWScgF.png" image_alt="KNN algorithm distance" image_title="KNN algorithm distance" %}

## Probability of classification of test value in KNN

It calculates the probability of test value to be in class `j` using this function

{% include math.html math_code="$P_r(Y=j|X=x_o) = \frac{1}{K}\sum_{i\epsilon N_o}I(y_i = j)$" style="margin-top:0.2em; margin-bottom:0.5em;" %}

## Ways to calculate the distance in KNN

The distance can be calculated using different ways which include these methods,

* Euclidean Method
* Manhattan Method
* Minkowski Method
* etc...

For more information on distance, please read [this post on KNN](https://www.saedsayad.com/k_nearest_neighbors.htm)

You can use any method from the list by passing `metric` parameter to the KNN object. Here is an answer on [Stack Overflow which will help](https://stackoverflow.com/questions/21052509/sklearn-knn-usage-with-a-user-defined-metric). You can even use some random distance metric.

Also [read this answer as well](https://stackoverflow.com/questions/34408027/how-to-allow-sklearn-k-nearest-neighbors-to-take-custom-distance-metric).

## The process of KNN with Example

Let's consider that we have a dataset containing heights and weights of dogs and horses marked properly. We will create a plot using weight and height of all the entries.

Now whenever a new entry comes in, we will choose a value of `k`.

For the sake of this example, let's assume that we choose 3 as the value of `k`. We will find the distance of nearest three values and the one having the least distance will have more probability and is assumed as the winner.



A good read that [benchmarks various options present in `sklearn` for Knn](https://jakevdp.github.io/blog/2013/04/29/benchmarking-nearest-neighbor-searches-in-python/)