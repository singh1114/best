---
layout: post
title: Normalizing or Standardizing distribution in Machine Learning
date: 2020-05-30T19:47:42.383Z
updated_date: 2020-05-30T19:47:42.399Z
description: How to Normalize or Standardize distribution in Machine Learning.
published: true
show_ads: false
include_mathjax: true
---
Normalizing and standardizing are the common concepts in statistics which help the data to bring under a common shelter without changing the relative difference between the different values present in data.

Does that sound odd? Don't worry keep going and you will know what I am talking about.

## Why do we want to Normalize the distribution

Let's first start with the `why` and then move to the further questions.

The values present with different features can vary a lot. For example, a `is_old` can have binary values(0 and 1) on the other hand a feature like `cost` can have values ranging from `$100` to `$10000` depending upon the item under consideration.

If we don't normalize/ Standardize your dataset feature having more range will contribute more toward the learning leading to bias in the model. In the above example, the `cost` value will contribute more toward the trained dataset.

We generally normalize values when feature are present in the dataset having different range.

*Normalization* doesn't lead to change in the real range of the dataset.

*Standardization* leads to reduction of dataset between values in such a way that mean of the distribution is set to 0 and standard deviation is set to 1. 

## How to normalize/ standardize distribution

A standard way to normalize a distribution is to apply this formula on each and every column.

{% include math.html math_code="$\frac{x - x_min}{x_max - x_min}$" style="margin-top:0.2em; margin-bottom:0.5em;" %}

This will distribute the values normally and reduce all the values between 0 and 1.

For standardization, we use the following formula,

{% include math.html math_code="$\frac{x - x_mean}{x_standard_deviation}$" style="margin-top:0.2em; margin-bottom:0.5em;" %}

## Apply Standardization on a dataset

Data source used: [GitHub of Data Source](https://github.com/singh1114/ml/blob/master/datascience/Machine%20learning/knn/KNN_Project_Data)

```python

# Import everything
import pandas as pd
import numpy as np

import matplotlib.pyplot as plt
import seaborn as sns
%matplotlib inline

# Create a DataFrame
df = pd.read_csv('KNN_Project_Data')

# Print the head of the data.
df.head()
```

{% include lazyload.html image_src="https://i.imgur.com/2bDtkX4.png" image_alt="KNN algorithm Head of dataframe" image_title="KNN algorithm Head of dataframe" %}

As we can already see that the data in the data frame is not standardized, if we don't normalize the data the outcome will be fairly different and we won't be able to get the correct results.

We can understand this concept in more detail if we think in terms of neural networks. Let's say we have a dataset and we are trying to find the salary of the employees given some features like, years of experience, grades in high school, university and salary in last organization different other factors.

Now if we keep the data as it is, some features having higher values will get higher importance. So, to give a fair chance to every feature to contribute equally toward the model initially( with fixed weights), we normalize the distribution.

Sklearn provides a very simple way to standardize your data.

```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
scaler.fit(df.drop('TARGET CLASS', axis=1))
sc_transform = scaler.transform(df.drop('TARGET CLASS', axis=1))
sc_df = pd.DataFrame(sc_transform)

# Now you can safely use sc_df as your input features.
sc_df.head()
```

{% include lazyload.html image_src="https://i.imgur.com/6ADY6NW.png" image_alt="KNN algorithm normalized data frame" image_title="KNN algorithm normalized data frame" %}

This standardization uses the values of mean and standard deviation to calculate the new as opposed to the one of the basic `min-max` approach we discussed earlier.

{% include lazyload.html image_src="https://i.ibb.co/8Ms1K4Y/Screenshot-2020-05-12-at-12-42-38-AM.png" image_alt="KNN algorithm StandardScaler normalization" image_title="KNN algorithm StandardScaler normalization" %}

## Apply Standardization on a dataset

```python
from sklearn.preprocessing import MinMaxScaler

minmaxscaler = MinMaxScaler()
minmaxscaler.fit(df.drop('TARGET CLASS', axis=1))
sc_transform = minmaxscaler.transform(df.drop('TARGET CLASS', axis=1))
sc_df = pd.DataFrame(sc_transform)
sc_df.head()
```

{% include lazyload.html image_src="https://i.ibb.co/WcL0TJC/Screenshot-2020-05-31-at-2-22-38-AM.png" image_alt="MinMaxScaler" image_title="MinMaxScaler" %}

This is how `MinMaxScaler` works in sklearn.

{% include lazyload.html image_src="https://i.ibb.co/D96pZQZ/Screenshot-2020-05-31-at-2-24-41-AM.png" image_alt="MinMaxScaler Sklearn" image_title="MinMaxScaler Sklearn" %}

The idea behind preprocessing modules in Sklearn is that, you can fit with any given data and then transform some different data to change the data according to one on which you fit it.

So, it is a general practice to fit the `StandardScaler` on the train data and transform on both train and test data.

Hope you liked the post. Leave a comment if you have any question. Also, do subscribe to the newsletter if you want to read more such posts.