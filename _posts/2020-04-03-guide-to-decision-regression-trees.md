---
layout: post
title: A Beginner's guide to Regression Trees using Sklearn | Decision Trees
date: 2020-04-03T21:05:13.718Z
updated_date: 2020-04-03T21:05:13.730Z
description: Beginner's guide to Regression Trees including the equation,
  Pruning, Prediction using stratification of features in decision Trees using
  sklearn.
published: true
image: https://i.ibb.co/vsJ5X6N/Main-Images-1.png
tags:
  - python
  - machinelearning
  - datascience
categories:
  - python
  - machinelearning
  - datascience
  - sklearn
show_ads: false
include_mathjax: true
---
{% include lazyload.html image_src="https://i.ibb.co/vsJ5X6N/Main-Images-1.png" image_alt="Regression Tree beginner's guide" image_title="Regression Tree beginner's guide" %}

Regression tree-based models produce the result (leaf node) gives the output as a real value.

For example, a model that try to predict the salary of baseball players using the data like, years of experience and number of hits that the hitter made in the last season.

## Greedy nature of decision trees

Almost all of the Decision Tree algorithm uses Greedy approach, that is, at every node generation, we don't care about the final tree becoming better. We are only worried about making the best split at any given time.

Let's understand this by taking the `Striker salary dataset` example.

To simplify the calculations, let's assume that we only have three features in the dataset, `Experience`, `Goals last season` and `Salary` and salary is the feature that we want to predict.

On this random data, we decided to fit the decision tree model. After initially analyzing the data, we found that `Experience` was the most usable factor which was clearly dividing the whole dataset into different parts.

So, rather than thinking of ahead in time, we will directly choose the `Experience` as the root node at this point.

We will discuss the above example much in detail during this post.

## Equation of Regression Tree

As we already know the equation of the linear regression model which is equal to the equation of a straight line. We also have an equation for Regression Tree.

{% include math.html math_code="$f(x) =\displaystyle \sum_{m=1}^{M} C_m.1(X \epsilon R_m)$" style="margin-top:0.2em;" %}

{% include math.html math_code="$where\ R_1, R_2...R_m\ are\ the\ different\ regions$" %}

## Predictions in Regression Trees

There are a few different ways in which we can predict a regression tree. In this post, we are going to discuss,

* Prediction using Stratification of feature space
* Prediction using Tree Pruning

## Prediction using stratification of feature space

As we have already discussed that while fitting trees we almost every time use the greedy approach. We will use the same approach here as well.

At any given time of node(branch feature) determination, we want to reduce the value of the `Residual Sum of Squares(RSS)`.

Mathematically the value is given by,

{% include math.html math_code="$For\ every\ y_i\ in\ the\ given\ region$" style="margin-top:0.2em;" %}

{% include math.html math_code="$RSS = \displaystyle \sum_{j=1}^{J} \sum_{i \epsilon R_j} (y_i - \widehat{y}_{R_j})^ {2}$" %}

{% include math.html math_code="$and\ \widehat{y}_{R_j}\ is\ mean\ value\ of\ training\ observations\ in\ Jth\ box.$" %}

Let's try to understand it using the `hitter's dataset`.

First, we plot the whole dataset onto a plan. For simplicity let's consider that all the points are confined in a rectangle.

In regression trees, at each point, we have to predict two values.

1. Value of the branch feature (node).
2. The cutoff value at which the reduction in RSS is minimum.

While working on the hitter's dataset, we found that `Age` was dividing the region in a better way. So, the branch feature(root node) that we chose was `Age`. Also, we found that the cutoff value of 4.5 years was giving optimal results.

We will apply the recursion and apply the same steps again. Since we now have two regions, `R1` with salaries of `hitters` with experience < 4.5 years and `R2` with experience >= 4.5 years.

We now chose from these two available regions and try to divide them. The only other available feature is `number of hits`. We found that there is a clear distinction between the salaries of hitters hitting `117+` hits last year in region `R2`.

Finally, we chose to leave the `R1` as it is as there was no clear advantage of dividing it further.

This is what our Regression tree will look like.

{% include lazyload.html image_src="https://i.ibb.co/7bsbNKn/Screenshot-2020-04-04-at-5-27-27-PM.png" image_alt="Regression Tree for hitters dataset" image_title="Regression Tree for hitters dataset" %}

Here the leaf nodes show the mean salary of all the hitters in the given region.

On the same lines, the region partition will look something like this.

{% include lazyload.html image_src="https://i.ibb.co/YfFCHDd/Screenshot-2020-04-04-at-6-37-55-PM.png" image_alt="Region partition for regression tree" image_title="Region partition for regression tree" %}

Mathematically,

In **recursive binary splitting**, we first select the predictor `Xj` and the cutoff value `S` such that,

{% include math.html math_code="$\{X|X_j < S\}\ and\ \{X|X_j \geq S\}$" %}

leads to the maximum reduction in the RSS.

So, the equation that we want to minimize is,

{% include math.html math_code="$\displaystyle \sum_{i:x_i\epsilon R_1(j, s)}(y_i - \widehat{y}_{R_1})^ {2} + \sum_{i:x_i\epsilon R_2(j, s)}(y_i - \widehat{y}_{R_2})^ {2}$" %}

This process of dividing one of the available region into smaller ones is repeated until we reach and endpoint or a proper regression value.

## Disadvantages of predicting using stratification

* This algorithm might produce good results in the training data but is likely to overfit the data, leading to poor test set performance. This happens because the tree is too complex.

Therefore, using this algorithm to create a model and then trying to understand it is quite tough when the number of features are high.

> Machine learning models try to find a sweet spot between the overfit and underfit so, that the error rate should be minimized and at the same time, it should be able to predict correctly.

## Predicting using Tree Pruning

Tree Pruning isn't only used for regression trees. We also make use of it in the classification trees as well.

As the word itself suggests, the process involves cutting the tree into smaller parts.

We can do pruning in two ways.

* **Pre-pruning or early stopping**

This means stopping before the full tree is even created. We can keep making the tree until the next node doesn't change the error rate change drastically. Whenever we see a very minor change in the error rate after building the next node, we can stop building further.

* **Post Pruning**

Creating the full tree up until we have very few data points in each set and then track backing such that the change in the error rate is not much.

Since, Tree pruning itself is a vast topic I have created a separate post for it. Please read that post if you want to know more about it.

{% include linked_post.html url="practical-approach-to-tree-pruning-using-sklearn" %}

## Regression Tree analysis using Sklearn

Let's import the required libraries

```python
import matplotlib.pyplot as plt

import numpy as np
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.datasets import load_boston
from sklearn.tree import DecisionTreeRegressor
from sklearn.metrics import mean_squared_error
```

We are using the `boston` data, which is the house pricing data of the Boston region. You can know more about the data by running

```python
print(load_boston().DESCR)
```

Split the data into training and testing set.

```python
X, y = load_boston(return_X_y=True)

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.33, random_state=42)
```

Fit the Regression Tree model and get the predictions.

```python
clf = DecisionTreeRegressor()
clf.fit(X_train, y_train)

predictions = clf.predict(X_test)

print(mean_squared_error(y_test, predictions))
print(np.sqrt(mean_squared_error(y_test, predictions)))
```

Results:

```python
18.59688622754491
4.312410721110051
```

## Finding the relation between Tree depth and Mean Square Error

We can train the model with different depth values using a simple Python loop and then plot a relation between them.

```python
mses = []
for depth in range(1, (clf.tree_.max_depth + 1)):
    d_tree_reg = DecisionTreeRegressor(max_depth=depth)
    d_tree_reg.fit(X_train, y_train)
    tree_predictions = d_tree_reg.predict(X_test)
    mses.append(mean_squared_error(y_test, tree_predictions))

tree_depths = [depth for depth in range(1, (clf.tree_.max_depth + 1))]
plt.figure(figsize=(10,  6))
plt.grid()
plt.plot(tree_depths, mses)
plt.xlabel("Tree Depth")
plt.ylabel("Mean Square Error")
```

{% include lazyload.html image_src="https://i.ibb.co/pjcwBcp/Screenshot-2020-04-06-at-9-57-50-PM.png" image_alt="Regression Tree relation between MSE and Tree Depth" image_title="Regression Tree relation between MSE and Tree Depth" %}

We can clearly see that if we define the depth of the tree equivalent to `6`, we will get the best results and minimum `Mean Square Error`.

Please share on social media and [subscribe](https://ranvir.xyz/blog/subscribe) to the newsletter to read more such posts.