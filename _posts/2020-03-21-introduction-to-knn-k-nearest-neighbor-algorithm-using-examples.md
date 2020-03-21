---
layout: post
title: Introduction to KNN | K-nearest neighbour algorithm using Examples
date: 2020-03-21T22:14:11.038Z
updated_date: 2020-03-21T22:14:11.051Z
published: true
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
`KNN` also known as K-nearest neighbour is a [supervised and classification learning algorithm](https://ranvir.xyz/blog/how-to-evaluate-your-machine-learning-model-like-a-pro-metrics/#supervised-learning-and-classification-problems) which helps us find which class the new input(test value) belongs to when `k` nearest neighbours are chosen and distance is calculated between them.

> It attempts to estimate the conditional distribution of `Y` given `X`, and classify a given observation(test value) to the class with highest estimated probability.

It first identifies the `k` points in the training data that are closest to the `test value` and calculates the distance between all those categories. The test value will belong to the category whose distance is the least.

{% include lazyload.html image_src="https://i.imgur.com/XXWScgF.png" image_alt="KNN algorithm distance" image_title="KNN algorithm distance" %}

## Probability of classification of test value in KNN

It calculates the probability of test value to be in class `j` using this function

{% include math.html math_code="$P_r(Y=j|X=x_o) = \frac{1}{K}\sum_{i\epsilon N_o}I(y_i = j)$" style="margin-top:0.2em; margin-bottom:0.5em;" %}