---
layout: post
title: How to evaluate your Machine learning model like a pro | Metrics
date: 2020-02-20T19:22:14.832Z
description: >-
  Evaluating of your machine learning model can be done using accuracy, recall,
  precision, F1-score and/or mean absolute error or mean square error.
published: false
tags:
  - machinelearning
  - datascience
  - python
categories:
  - machinelearning
  - datascience
  - python
---
You are happy with your Machine Learning model. You go up to your clients and show them the new model. You are excited to run it on the new production data. Checking your eagerness, client asks this question.

> How accurate is your model?

What should be your answer to this question?

Today we are going to talk about the problem of calculating the accuracy of your model along with some code samples that will help you to calculate them easily.

## What is the process of evaluating your model?

So, Machine Learning is a simple way of predicting the results with the input that model has not seen before. For example, Predicting stock prices with the historical data related to that particular stock which can tell us, whether it would be profitable to buy a stock on particular day or not.

Evaluating a model is like checking the accuracy of model when test data is passed onto the model - a piece of data which the model has never seen before.

## Why do we need to evaluate our model?

In general, it is a good metric to come up with when we are talking about your model with the guys in other teams who don't understand tech.

No model is 100% correct and there is no perfect score you want to achieve. It simply depends on case to case basis. Also, sometimes giving wrong answer is better than giving very wrong answer.

For example if you are building a cancer detector depending upon the test reports of the patient. You might want to tell the patient might have `cancer` and finally get off with the real cancer test, rather than giving `no cancer` output from your model, when in reality the person had cancer.

## Supervised learning and classification problems.

`Supervised Learning` are the problems where the outcomes of the model are already known. For example a data set of housing prices of an area.

`Classification Problem` are a subset of supervised learning where the outcomes are generally divided into two or more parts. For example whether a person is having cancer or not.

All these models can be evaluated on the following parameters.

Generally we divide the total dataset into two parts. First dataset is known as the training data and the other is known as the test data.

The idea behind such division of the data is to use test data just for evaluation purposes. To find if the model we are trying to use for the given dataset is good enough, or we want to use a different one.

Here is a code sample which can help you to divide your [data frame](https://ranvir.xyz/blog/data-science-ii-introduction-to-pandas/#dataframes-in-pandas) into several parts using [scikit-learn](https://scikit-learn.org/stable/).

```python
import pandas as pd
from sklearn.model_selection import train_test_split

df = pd.read_csv('Ecommerce Customers')

X = df[['Avg. Session Length', 'Time on App', 'Time on Website', 'Length of Membership']]
y = df['Yearly Amount Spent']

df = pd.read_csv('Ecommerce Customers')

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3)
```

`test_size` is the amount of data that you want to your test split to be. `0.3` means that the test split would be 30%.

## Accuracy

Accuracy is the simple calculation where you divide number of data points evaluated correctly by the number of total data points.

{% include math.html math_code="$accuracy = \frac{number\ of\ correct\ responses}{Total\ number\ of\ test\ cases}$" %}

## Recall

## Precision

## F1-score

## Confusion matrix

## Evaluating for regression problems

## Mean Absolute error

## Mean Square error

## Root mean square error

## What is considered as a good metric for your model?
