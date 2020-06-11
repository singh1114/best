---
layout: post
title: Introduction to KNN | K-nearest neighbor classification algorithm using
  Examples
date: 2020-03-22T18:30:00.000Z
updated_date: 2020-03-22T18:30:00.000Z
description: Introduction to K-nearest neighbor( KNN) algorithm using sklearn.
  Using different distance metrics and why is it important to normalize KNN
  features?
published: true
image: https://i.imgur.com/3rMdVO4.png
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
show_ads: true
canonical_url: ""
include_mathjax: true
---
`KNN` or K-nearest neighbor classification algorithm is used as [supervised and pattern classification learning algorithm](https://ranvir.xyz/blog/how-to-evaluate-your-machine-learning-model-like-a-pro-metrics/#supervised-learning-and-classification-problems) which helps us to find which class the new input(test value) belongs to when `K` nearest neighbors are chosen using distance measure.

{% include lazyload.html image_src="https://i.imgur.com/3rMdVO4.png" image_alt="KNN algorithm python" image_title="KNN algorithm using sklearn" %}

> It attempts to estimate the conditional distribution of `Y` given `X`, and classify a given observation(test value) to the class with highest estimated probability.

The distance measure is used to find the `K` nearest neighbours. Once those `K` nearest neighbours are found, the new `test value` is assigned to the category having the largest number of elements out of those `K` neighbours.

{% include lazyload.html image_src="https://i.imgur.com/XXWScgF.png" image_alt="KNN algorithm distance" image_title="KNN algorithm distance" %}

## Probability of classification of test value in KNN

It calculates the probability of test value to be in class `j` using this function

{% include math.html math_code="$P_r(Y=j|X=x_o) = \frac{1}{K}\sum_{i\epsilon N_o}I(y_i = j)$" style="margin-top:0.2em; margin-bottom:0.5em;" %}

## Ways to calculate the distance in KNN

As already discussed that we have to calculate the distance between different points, we have a number of ways in which the distance can be  calculated, the most common being the `Euclidean` one, which I believe most of us have studied in high school.

* Euclidean Method
* Manhattan Method
* Minkowski Method
* etc...

For more information on distance metrics which can be used, please read [this post on KNN](https://www.saedsayad.com/k_nearest_neighbors.htm).

Minkowski is the one that is used by default.

{% include lazyload.html image_src="https://i.ibb.co/YPMYNXV/Screenshot-2020-05-11-at-11-48-50-PM.png" image_alt="KNN using minkowski" image_title="KNN using minkowski" %}

You can use any distance method from the list by passing `metric` parameter to the KNN object. Here is an answer on [Stack Overflow which will help](https://stackoverflow.com/questions/21052509/sklearn-knn-usage-with-a-user-defined-metric). You can even use some random distance metric.

Also [read this answer as well](https://stackoverflow.com/questions/34408027/how-to-allow-sklearn-k-nearest-neighbors-to-take-custom-distance-metric) if you want to use your own method for distance calculation.

Using different distance metric can have a different outcome on the performance of your model.

## The process of KNN with Example

Let's consider that we have a dataset containing heights and weights of dogs and horses marked properly. We will create a plot using weight and height of all the entries.

Now whenever a new entry comes in from the test dataset, we will choose a value of `k`.

For the sake of this example, let's assume that we choose 4 as the value of `k`. We will use the distance measure to find the `K` nearest neighbour and the `test value` will belong to the one having more number of entities out of those `K` neighbours.

{% include lazyload.html image_src="https://i.imgur.com/heaLl5s.png" image_alt="KNN algorithm example" image_title="KNN algorithm example" %}

## KneighborsClassifier: KNN Python Example

GitHub Repo: [KNN GitHub Repo](https://github.com/singh1114/ml/blob/master/datascience/Machine%20learning/knn/knn.ipynb)

Data source used: [GitHub of Data Source](https://github.com/singh1114/ml/blob/master/datascience/Machine%20learning/knn/KNN_Project_Data)

In K-nearest neighbors algorithm most of the time you don't really know about the meaning of the input parameters or the classification classes available.

In case of interviews, you will get such data to hide the identity of the customer.

You can use the following code to load it into a `DataFrame`.

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

The head of the data clearly says that we have a few variables and a target class that contain different classes for given parameters.

### Why normalize/ standardize the variables for KNN

As we can already see that the data in the data frame is not standardized, if we don't standardize it, the outcome will be fairly different and we won't be able to get the correct results.

This happens because some feature has a good amount of deviation in them (values range from 1-1000 vs values ranging from 1-10). This will lead to a bias in the model.

We can understand this concept in more detail if we think in terms of neural networks. Let's say we have a dataset and we are trying to find the salary of the employees given some features like, years of experience, grades in high school, university and salary in last organization different other factors.

Now if we keep the data as it is, some features having higher values will get higher importance. So, to give a fair chance to every feature to contribute equally toward the model initially( with fixed weights), we normalize the distribution.

A standard way to normalize a distribution is to apply this formula on each and every column.

{% include math.html math_code="$\frac{x - min}{max - min}$" style="margin-top:0.2em; margin-bottom:0.5em;" %}

This will distribute the values normally and reduce all the values between 0 and 1.

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

This is better because it will account for the deviation in the data.

{% include lazyload.html image_src="https://i.ibb.co/8Ms1K4Y/Screenshot-2020-05-12-at-12-42-38-AM.png" image_alt="KNN algorithm StandardScaler normalization" image_title="KNN algorithm StandardScaler normalization" %}

For more information on Normalization and Standardization read the following post.

{% include linked_post.html url="normalize-standardize-distribution-in-machine-learning" %}

### Test/Train split using sklearn

We can simply [split the data using sklearn](https://ranvir.xyz/blog/how-to-evaluate-your-machine-learning-model-like-a-pro-metrics/#test-train-split-using-sklearn).

```python
from sklearn.model_selection import train_test_split

X = sc_transform
y = df['TARGET CLASS']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3)
```

### Using KNN and finding an optimal k value

Choosing a good value of `k` can be a daunting task. We are going to automate this task using Python. We were able to find a good value of `k` which can minimize the error rate in the model.

```python
# Initialize an array that stores the error rates.
from sklearn.neighbors import KNeighborsClassifier

error_rates = []

for a in range(1, 40):
    k = a
    knn = KNeighborsClassifier(n_neighbors=k)
    knn.fit(X_train, y_train)
    preds = knn.predict(X_test)
    error_rates.append(np.mean(y_test - preds))

plt.figure(figsize=(10, 7))
plt.plot(range(1,40),error_rates,color='blue', linestyle='dashed', marker='o',
         markerfacecolor='red', markersize=10)
plt.title('Error Rate vs. K Value')
plt.xlabel('K')
plt.ylabel('Error Rate')
```

{% include lazyload.html image_src="https://i.imgur.com/j4EsgY8.png" image_alt="Finding optimal k value" image_title="Finding optimal k value" %}

Seeing the graph, we can see that `k=30` gives a very optimal value of error rate.

```python
k = 30
knn = KNeighborsClassifier(n_neighbors=k)
knn.fit(X_train, y_train)
preds = knn.predict(X_test)
```

## Evaluating the KNN model

Read the following post to learn more about evaluating a machine learning model.

{% include linked_post.html url="how-to-evaluate-your-machine-learning-model-like-a-pro-metrics" %}

```python
from sklearn.metrics import confusion_matrix, classification_report

print(confusion_matrix(y_test, preds))
print(classification_report(y_test, preds))
```

{% include lazyload.html image_src="https://i.imgur.com/Iu5PoLx.png" image_alt="confusion matrix and classification report" image_title="confusion matrix and classification report" %}

## Benefits of using KNN algorithm

* KNN algorithm is widely used for different kinds of learnings because of its uncomplicated and easy to apply nature.
* There are only two metrics to provide in the algorithm. value of `k` and `distance metric`.
* Work with any number of classes not just binary classifiers.
* It is fairly easy to add new data to algorithm.

## Disadvantages of KNN algorithm

* The cost of predicting the `k` nearest neighbors is very high.
* Doesn't work as expected when working with a big number of features/parameters.
* Hard to work with categorical features.

A good read that [benchmarks various options present in sklearn for Knn](https://jakevdp.github.io/blog/2013/04/29/benchmarking-nearest-neighbor-searches-in-python/)

Hope you liked the post. Feel free to share any issues or any questions that you have in the comments below.