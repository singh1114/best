---
layout: post
title: How to choose a good evaluation metric for your Machine learning model
date: 2020-02-20T19:22:14.832Z
updated_date: 2020-04-10T18:30:00.000Z
description: Evaluating your machine learning model can be done using accuracy,
  recall, precision, F1-score and/or mean absolute error or mean square error.
published: true
image: https://i.imgur.com/oWQcLd6.png
tags:
  - machinelearning
  - datascience
  - python
categories:
  - machinelearning
  - datascience
  - python
show_ads: false
include_mathjax: true
redirect_from: []
---
{% include lazyload.html image_src="https://i.imgur.com/oWQcLd6.png" image_alt="evaluate your Machine learning model like a pro" image_title="evaluate your Machine learning model like a pro" %}

You are happy with your Machine Learning model and excited to share it with your client. You go up to your clients and show them the new model. You are excited to run it on the new production data. Checking your eagerness, the client asks this question.

> How accurate is your model?

What should be your answer to this question?

Today we are going to talk about the problem of calculating the accuracy of your model along with some code samples that will help you to calculate them easily.

At the end of the post, you will be able to know and understand all the ways of evaluating your machine learning model.

## What is the process of evaluating your model?

{% include lazyload.html image_src="https://i.imgur.com/ivfxqsd.png" image_alt="Machine learning model evaluation process" image_title="Machine learning model evaluation process" %}

So, Machine Learning is a simple way of predicting the results with the input that the model has not seen before. For example, Predicting stock prices with the historical data related to that particular stock which can tell us, whether it would be profitable to buy a stock on a particular day or not.

Evaluating a model is like checking the accuracy of the model when test data is passed onto the model - a piece of data that the model has never seen before.

## Why do we need to evaluate our model?

In general, it is a good metric to come up with when we are talking about your model with the guys in other teams who don't understand tech.

No model is 100% correct and there is no perfect score you want to achieve. It simply depends on case to case basis. Also, sometimes giving the wrong answers is better than giving a very wrong answer.

For example, if you are building a cancer detector depending upon the test reports of the patient. You might want to tell that the patient might have `cancer` and finally get off with the real cancer test, rather than giving `no cancer` output from your model when in reality the person had cancer.

## Supervised learning and classification problems.

`Supervised Learning` are the problems where the outcomes of the model are already known. For example a data set of housing prices of an area.

`Classification Problem` is a subset of supervised learning where the outcomes are generally divided into two or more parts. For example, whether a person is having cancer or not.

All these models can be evaluated on the following parameters.

### Test train split using sklearn

Generally, we divide the total dataset into two parts. The first dataset is known as the training data and the other is known as the test data.

The idea behind such a division of the data is to use test data just for evaluation purposes. To find if the model we are trying to use for the given dataset is good enough, or we want to use a different one.

Here is a code sample that can help you to divide your [data frame](https://ranvir.xyz/blog/data-science-ii-introduction-to-pandas/#dataframes-in-pandas) into several parts using [scikit-learn](https://scikit-learn.org/stable/).

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

Accuracy is the simple calculation where you divide the number of data points evaluated correctly by the number of total data points.

{% include math.html math_code="$accuracy = \frac{number\ of\ correct\ responses}{Total\ number\ of\ test\ cases}$" style="margin-top:0.2em; margin-bottom:0.5em;" %}

We first calculate the `predictions` corresponding to the given `X_test`, finally, we compare these predictions with the `y_test` which are the real outcomes to the corresponding parameters.

We will talk more about how we calculate these values in [later posts](https://ranvir.xyz/blog/machinelearning/). Keep track of the progress by [subscribing](https://ranvir.xyz/blog/subscribe).

Accuracy is one of the easiest ways to evaluate the performance of your model.

**Note:** This type of evaluation model is not the best thing to use when the data available to you is unbalanced.

> Unbalanced data is the type of dataset in which you have more outcomes for one type of data and fewer outcomes for others.

For example In a cat-dog images dataset, out of 100 pictures, you have 90 pictures of dog and 10 pictures of cat.

In such case, if you are checking the accuracy for dog pictures and your model always return `dog`, no matter what picture is thrown at it, the accuracy in any case will be `90%`.

## Recall

> It is the ability of your model to find all the relevant cases in your model.

Most of these evaluation models are used when the data in [mainly imbalanced](http://www.chioka.in/class-imbalance-problem/).

{% include math.html math_code="$recall = \frac{number\ of\ true\ positives}{number\ of\ true\ positives + No.\ of\ false\ Negatives}$" %}

In a case of a model that classifies every volcano to erupt the next day having a data set with 20% values of it erupting the next day, The value of recall will look something like this.

{% include math.html math_code="$recall = \frac{volcanos\ correctly\ identified}{volcanos\ correctly\ identified + volcanos\ incorrectly\ labelled\ to\ not\ erupt\ tomorrow}$" style="margin-top:0.2em;" %}

{% include math.html math_code="$recall = \frac{20}{20 + 0}$" %}

{% include math.html math_code="$recall = 1$" style="margin-bottom:0.2em;" %}

Although the value of `recall` is great, it goes with the value of `precision` and in most cases both of their value is considered.

## Precision

> Ability of a model to identify only the relevant data points.

{% include math.html math_code="$precision = \frac{number\ of\ true\ positives}{number\ of\ true\ positives + No.\ of\ false\ Positives}$" style="margin-top:0.2em; margin-bottom:0.2em;" %}

According to the same volcano problem,

{% include math.html math_code="$precision = \frac{volcanos\ correctly\ identified}{volcanos\ correctly\ identified + volcanos\ incorrectly\ labelled\ to\ erupt\ tomorrow}$" style="margin-top:0.2em;" %}

{% include math.html math_code="$precision = \frac{20}{20 + 80}$" %}

{% include math.html math_code="$precision = 0.2$" style="margin-bottom:0.2em;" %}

In general, it is a standard to maximize both the values of recall and precision.

## Accuracy vs Recall using Example.

Choosing what you want as your evaluation metric really depends upon the problem that you are trying to solve. I will take a few examples that will help you decide when to use the first and when to use the next.

### Case 1: Disease detection (Covid 19)

Let's say you are working on a model that is trying to detect whether the person is having [COVID 19](https://en.wikipedia.org/wiki/Coronavirus_disease_2019).

In this particular case, the cost of `False Negative` is more than the cost of `False Positive`. Hence, if you predict that someone is not having a disease when someone is actually carrying one will lead to some bad circumstances. They might go out and start spreading it.

On the other hand, if you predict someone not really carrying the disease when in reality he/she is a disease carrier, it is not a big of an issue, because we will obviously do further tests on them.

In this case, we will try to lower the result of our evaluation metric when the number of false negatives is increasing. Looking at the formulas of `Recall` and `Accuracy`, we know that the thing that we want to use is, `Recall`.

### Case 2: Email Detection (Spam or Not spam)

In this problem, the cost of `False Positive` is more than the cost of `False Negative`.

If your models start predicting important mails as spam and start sending them to the spam folder, it would be really bad. So, in this case, you will want to choose a metric that will lower its value when the number of False positives starts increasing.

Again we know the right metric for such a problem is `Precision`.

## F1-score

> It is the harmonic mean of precision and recall.

F1-score helps us to consider both the values of precision and recall while evaluating our model.

{% include math.html math_code="$F1-score = \frac{2 * precision * recall}{precision * recall}$" %}

## Confusion matrix

Confusion matrix is a Matrix in which we evaluate all the positives and negatives like:

* True Positive
* False Positive
* True Negative
* False Negative

It also helps you to evaluate your machine learning model in a better way.

{% include lazyload.html image_src="https://i.imgur.com/YE8Ohhl.png" image_alt="confusion matrix to evaluate your machine learning model" image_title="confusion matrix to evaluate your machine learning model" %}

The image shows the `confusion matrix` for a case where patient's data was tested for a specific disease. Out of total 165 patients our model produced the following results.

**True Positives:** Our model predicted that 100 patients were carrying the disease, and they were actually carrying the disease.

**True Negatives:** Our model predicted that 50 patients were not carrying the disease, and they actually were not carrying it.

**False Positives:** Our model predicted that 10 patients were carrying the disease, and they actually were not carrying it. This is also known as **Type-I error**.

**False Negatives:** Our model predicted that 5 patients were not carrying the disease, and they actually were carrying it. This is also known as **Type-II error**.

We can go forward and calculate all the values for Accuracy, Recall, Precision and F1-Score from this confusion matrix.

To print the confusion matrix of a model in `sklearn` use the following code.

```python
from sklearn.metrics import confusion_matrix

print(confusion_matrix(y_test, predictions))

# where y_test is the data frame of test values
# and predictions are the model predicted values
```

You can also print a matrix containing all values like `recall`, `precision` etc. using the following code,

```python
from sklearn.metrics import classification_report

print(classification_report(y_test, predictions))
```

{% include lazyload.html image_src="https://i.imgur.com/Iu5PoLx.png" image_alt="confusion matrix and classification report" image_title="confusion matrix and classification report" %}

For more information, read the following post

{% include linked_post.html url="k-nearest-neighbor-algorithm-using-sklearn-distance-metric" %}

## Evaluating for regression problems

Regression problems are a little different from the categorization problems as the output is just not a single value. Here you can actually see how off your predicted value was from the real value.

Here are the three ways in which regression models can be evaluated.

## Mean Absolute Error

Its a simple difference between the predicted and the actual values. Here is the simplest way in which you can calculate Mean Absolute error for your model.

{% include math.html math_code="$MAE = \frac{1}{n}\sum\left | Y_a - Y_e \right |$" style="margin-top:0.2em;" %}

{% include math.html math_code="$where\ Y_a\ is\ the\ actual\ value$" %}

{% include math.html math_code="$and\ Y_e\ is\ the\ model\ evaluated\ value$" style="margin-bottom:0.5em;" %}

You can get the value in using `sklearn` using the following code.

```python
from sklearn import metrics

metrics.mean_absolute_error(y_test, predictions)
```
The only problem with this model is that it doesn't punish the outliers. If a value is very far from the current value, it will not punish it and the error will get averaged out by other values.

{% include lazyload.html image_src="https://i.imgur.com/rFK2Kpl.png" image_alt="Machine learning model regression evaluation" image_title="Machine learning regression evaluation" %}

## Mean Square Error

Mean square error is the sum of squared errors of the predicted and actual values.

{% include math.html math_code="$MSE = \frac{1}{n}\sum (Y_a - Y_e)^{2}$" style="margin-top:0.2em;" %}

You can get the value in using `sklearn` using the following code.

```python
from sklearn import metrics

metrics.mean_squared_error(y_test, predictions)
```

The only problem with this value is that you can't really make any sense of the value. For example, you can't really tell that our model is `100 square unit` accurate.

## Root Mean Square Error

To solve the problem with the `MSE`, we use `RMSE` just by square rooting the values of `MSE`. We can then simply tell about the proficiency of our model from the value derived from this.

{% include math.html math_code="$RMSE = \sqrt{\frac{1}{n}\sum (Y_a - Y_e)^{2}}$" style="margin-top:0.2em;" %}

You can calculate this is Python using [Numpy](https://ranvir.xyz/blog/data-science-i-all-things-you-need-to-know-about-numpy/) and `sklearn`.

```python
from sklearn import metrics

np.sqrt(metrics.mean_squared_error(y_test, predictions))
```

## What is considered as a good metric value for your model?

As we have already discussed a good metric value of the model really depends upon the type model you are evaluating. You will always have to check with the peers who really are going to use your model.

Hope you liked the post, do leave your thoughts on what you use to evaluate your model and what do you think is a good metric value for your model.
