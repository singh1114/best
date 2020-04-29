---
layout: archive
title: Confusion Matrix in Machine Learning using sklearn
date: 2020-04-29T15:30:22.238Z
updated_date: 2020-04-29T15:30:22.259Z
description: Confusion Matrix is a 2X2 matrix which is used to evaluate a
  machine learning model. It is used to measure the performance of the model.
published: true
tags:
  - python
  - sklearn
  - machinelearning
  - datascience
categories:
  - python
  - sklearn
  - machinelearning
  - datascience
show_ads: false
---
Confusion Matrix is a `2X2` matrix which is used to evaluate a machine learning model. It is used to measure the performance of the model. It also helps you to evaluate your machine learning model in a better way and makes it easy to calculate recall, precision, f1-score, ROC curves etc.

Before jumping in we need to know a few terms.

* True Positive
* False Positive
* True Negative
* False Negative

We will explain these terms in context of an example.

Let's consider that we are creating a model which can detect if the person has COVID-19.

## True Positive

If our model detects someone to be COVID-19 positive and the person really was positive as well.

## False Positive

If our model detect someone to be COVID-19 positive but the person was not positive.

## True Negative

If our model detect someone to be COVID-19 negative and the person was not positive.

## False Negative

If our model detect someone to be COVID-19 negative but the person was positive.

{% include lazyload.html image_src="https://i.imgur.com/YE8Ohhl.png" image_alt="confusion matrix to evaluate your machine learning model" image_title="confusion matrix to evaluate your machine learning model" %}

The image shows the `confusion matrix` for a case where patient's data was tested for COVID-19. Out of total 165 patients our model produced the following results.

**True Positives:** Our model predicted that 100 patients were carrying the disease, and they were actually carrying the disease.

**True Negatives:** Our model predicted that 50 patients were not carrying the disease, and they actually were not carrying it.

**False Positives:** Our model predicted that 10 patients were carrying the disease, and they actually were not carrying it. This is also known as **Type-I error**.

**False Negatives:** Our model predicted that 5 patients were not carrying the disease, and they actually were carrying it. This is also known as **Type-II error**.

We can go forward and calculate all the values for Accuracy, Recall, Precision and F1-Score from this confusion matrix using these values.

## Using sklearn to print confusion Matrix

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

{% include linked_post.html url="how-to-evaluate-your-machine-learning-model-like-a-pro-metrics" %}
