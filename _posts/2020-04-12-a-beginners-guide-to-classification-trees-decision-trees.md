---
layout: post
title: A Beginner's guide to classification Trees | Decision Trees
date: 2020-04-11T21:43:43.067Z
updated_date: 2020-04-11T21:43:43.090Z
published: true
tags:
  - python
  - machinelearning
  - datascience
  - sklearn
categories:
  - python
  - machinelearning
  - datascience
  - sklearn
show_ads: false
include_mathjax: true
---
Classification Trees are the trees in which we classify the values as the output of the model.

For example, predicting that a customer is worthy of giving out the loan or not using the data of his salary and other credit history.

{% include lazyload.html image_src="https://i.ibb.co/cDS9RN7/Screenshot-2020-04-04-at-12-14-54-AM.png" image_alt="Loan Provider company decision Tree" image_title="Loan Provider company decision Tree" %}

Classification tree algorithms are generally divided into two parts.

1. Bagging Algorithms
2. Boosting Algorithms

Let's hold this thought for a while and discuss the most general terms which you will hear a lot while people are talking about decision trees.

As we already know from our previous discussion on Regression Trees, that tree algorithms are Greedy in nature which means they tend to choose the better node now, rather than choosing a node which will create a better tree later.

Also, in contrast to regression tree where predicted response of any given node is the mean of all the observations in the region, in classification trees predicted response is the most commonly occurring observation in the region to which it belongs.

Read the following post for more details.

{% include linked_post.html url="guide-to-decision-regression-trees" %}

In that post, we discussed RSS( Residual Sum of Squares)](https://ranvir.xyz/blog/guide-to-decision-regression-trees/#prediction-using-stratification-of-feature-space) which is the value that we want to maximize while building the regression tree.

Of course, we can't use RSS in classification trees.

We have similar terms in Classification trees that we can use. We can choose either one of these. These terms are used to quantify the split that we made.

1. Classification Error rate
2. Entropy
3. Gini Index

## Classification Error Rate for Classification Trees

Classification Error rate is simply the fraction of the training observations in that region that do not belong to the most common class.

Mathematically,

{% include math.html math_code="$E = 1 - max(p(k))$" style="margin-top:0.2em;" %}

{% include math.html math_code="$Where\ p(k)\ is\ the\ proportion\ of\ training\ observations\ in\ the\ mth\ region\ that\ are\ from\ the\ kth\ class$" %}

Classification Error rate is not used generally because it is not sensitive for tree-growing, therefore, entropy or Gini index is used instead.

## Entropy in Classification tree

It's the measure of amount of uncertainty of the data(Randomness). Higher the uncertainty, higher is the entropy.

The value of entropy is `zero` when there is no uncertainty in some event. For example, if we are tossing a coin having heads on both side.

Mathematically, entropy is given by

{% include math.html math_code="$H(s) =\displaystyle \sum_{x \epsilon X} p(x) log_2 \frac{1}{p(x)}$" style="margin-top:0.2em;" %}

{% include math.html math_code="$where\ p(x)\ is\ the\ proportion\ of\ occurring\ of\ some\ event$" %}

For example, for a simple coin toss the probability is `1/2`.

## Information Gain in classification trees

This is the amount of value gained for a given set `S`, when some feature `A` is selected as a node of the tree.

While selecting any node for the tree generation we want to maximize the Information Gain at that given point.

Information gain is given as the change in the Entropy before and after selecting any given feature as the node of tree.

Mathematically, it is given as,

{% include math.html math_code="$IG(S, A) = H(s) - H(S, A)$" style="margin-top:0.2em;" %}

{% include math.html math_code="$IG(S, A) = H(s) - \displaystyle \sum_{i=0}^{n} P(x) * H(x)$" %}

{% include math.html math_code="$where\ H(S)\ is\ the\ Entropy\ of\ entire\ Set$" %}

{% include math.html math_code="$and\ \sum_{i=0}^{n} p(x) * H(x)\ is\ the\ Entropy\ after\ applying\ feature\ x\ where\ P(x)\ is\ the\ proportion\ of\ event\ x$" %}

We will discuss it further while creating the model using Information Gain.

> Information gain is the count of entropy that we removed after adding a node to the tree.

## Gini Index in Classification Trees

This is the default metric that the Sklearn classifier tends to increase. 

It is used to quantify the split made in the tree at any given moment of node selection.

Mathematically, gini index is given by,

{% include math.html math_code="$G = \displaystyle \sum_{k=1}^{K} P(k)(1 - P(k))$" style="margin-top:0.2em;" %}

{% include math.html math_code="$Where\ P(k)\ is\ the\ proportion\ of\ training\ instances\ with\ class\ k$" %}

> Minimum value that the Gini index can get is 0.

For example, A coin having heads on both sides will give Gini Index as 0.

{% include math.html math_code="$(1 * (1 - 1)) = 0$" style="margin-top:0.2em;" %}

Gini index also tells about the purity of node selection. If a node selected is very pure the value of Gini index will be low.

## Gini Gain in Classification Trees

As we have information gain in the case of entropy, we have Gini Gain in case of Gini index.

It is the amount of gini index we gained when a node is chosen for the decision tree.

We will take an example to understand these terms in little more detail.

Let's consider a following data source,

| Outlook  | Temperature | Humidity | Wind   | Played |
|----------|-------------|----------|--------|--------|
| Sunny    | Hot         | High     | Weak   | No     |
| Sunny    | Hot         | High     | Strong | No     |
| Overcast | Hot         | High     | Weak   | Yes    |
| Rain     | Mild        | High     | Weak   | Yes    |
| Rain     | Cold        | Normal   | Weak   | Yes    |
| Rain     | Cold        | Normal   | Strong | No     |
| Overcast | Cold        | Normal   | Strong | Yes    |
| Sunny    | Mild        | High     | Weak   | No     |
| Sunny    | Cool        | Normal   | Weak   | Yes    |
| Rain     | Mild        | Normal   | Weak   | Yes    |
| Sunny    | Mild        | Normal   | Strong | Yes    |
| Overcast | Mild        | High     | Strong | Yes    |
| Overcast | Hot         | Normal   | Weak   | Yes    |
| Rain     | Mild        | High     | Strong | No     |

