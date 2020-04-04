---
layout: post
title: A Beginner's guide to Regression Trees | Decision Trees
date: 2019-07-23T21:05:13.718Z
updated_date: 2020-04-03T21:05:13.730Z
published: true
include_mathjax: true
---
Regression tree based models produce result (leaf node) gives the output as a real value.

For example a model which try to predict the salary of baseball players according to the data like, years of experience and number of hits that the hitter made in the last season.

## Greedy nature of decision trees

Almost all of the Decision Tree algorithm uses Greedy approaches that is, at every node generation, we don't care about the final tree become better. We are only worried about making the best split at any given time.

Let's understand this by taking the `Striker goals dataset` example.

To simplify the calculations, let's assume that we only have three features in the dataset, `Experience`, `Goals last season` and `Salary` and salary is the feature that we want to predict.

On this random data, we decided to fit the decision tree model. After initially analyzing the data, we found that `Experience` was the most usable factor which was clearly dividing the whole dataset into different parts.

So, rather than thinking of ahead in time, we will directly choose the `Experience` as the root node at this point.

We will discuss the above example much in detail during this post.

## Equation of Regression Tree

As we already know the equation of linear regression model which is equal to equation of a straight line. We also have an equation for Regression Tree.

{% include math.html math_code="$f(x) = \sum_{m=1}^{M} C_m.1(X \epsilon R_m)$" style="margin-top:0.2em;" %}

{% include math.html math_code="$where R_1,  R_2, ..., R_m\ are\ the\ different\ regions$" %}

## Predictions in Regression Trees

There are a few different ways in which we can predict a regression tree. In this post we are going to discuss,

* Prediction using Stratification of feature space
* Prediction using Tree Pruning

## Prediction using stratification of feature space

As we have already discussed that while fitting trees we almost every time use greedy approach. We will use the same approach in here as well.

At any given time of node(branch feature) determination, we want to reduce the value of Residual Sum of Squares(RSS).

Mathematically the value is given by,

{% include math.html math_code="$For\ every\ y_i\ in\ the\ given\ region$" style="margin-top:0.2em;" %}

\\
\sum_{j=1}^{J} \sum_{i \epsilon R_j} (y_i - \widehat{y}_R_j)^{2} 
\\
where\ \widehat{y}_R_j\ is\ the\ mean\ response\ of\ traning\ observations\ within\ the\ Jth\ box.