---
layout: post
title: SVM | Introduction to Support Vector Machines with Sklearn in Machine Learning
date: 2020-04-27T18:13:23.661Z
updated_date: 2020-04-27T18:13:22.829Z
description: SVM or support vector machines are supervised learning models that
  analyze data and recognize patterns on its own. They are used for both
  classification and regression analysis. In this post we are going to talk
  about Hyperplanes, Maximal Margin Classifier, Support vector classifier,
  support vector machines and will create a model using sklearn.
published: true
image: https://i.ibb.co/jyDFHsC/Main-Images-2-1.png
tags:
  - machinelearning
  - datascience
  - python
  - sklearn
categories:
  - machinelearning
  - datascience
  - python
  - sklearn
show_ads: false
include_mathjax: true
author_name: Ranvir Singh
author_username: ranvir_xyz
canonical_url: https://ranvir.xyz/blog/how-does-django-validate-passwords/
---
SVM or support vector machines are [supervised learning models](https://ranvir.xyz/blog/how-to-evaluate-your-machine-learning-model-like-a-pro-metrics/#supervised-learning-and-classification-problems) that analyze data and recognize patterns on its own. They are used for both classification and regression analysis.

An SVM model is the representation of the dataset as points in space so that the example of the separate categories is divided by a clear gap which is as wide as possible.

Any new incoming data is then mapped to one of these few categories based on which side of the gap they fall on.

{% include lazyload.html image_src="https://i.ibb.co/XYgV0Yg/Screenshot-2020-04-25-at-9-02-13-PM.png" image_alt="Two dimensional SVM example" image_title="Two dimensional SVM example" %}

For example, in the above image, we can clearly see that there are two categories in the dataset. Category blue and category pink.

Our aim is to differentiate between the two categories. One simple way of doing that is to draw a line between the two categories. But as we can see, there is an infinite number of lines that can clearly divide the dataset into two parts.

What we actually do is that we can choose a hyperplane that maximizes the margin between the classes. The data points (Vectors) touching the two outer lines are called support vectors.

This simple example of two-dimension linear plots can be further used in a dataset having more dimensions. Each time our idea will be to draw a hyperplane that can divide the data into different categories.

Now we are going to talk about some related mathematics and discuss different terms related to SVM.

In general, the discussion of SVM is divided into three parts according to how SVM evolved.

* Maximal Margin Classifier
* Support Vector Classifier
* Support Vector Machine

We will slowly move the article toward the Support Vector Machine but for a proper understanding of SVM's we have to go through, Maximal Margin Classifier and Support Vector Classifier.

## Maximal Margin Classifier
----

Maximal Margin Classifier is a model that is used to classify the observations into two parts using a hyperplane.

### What is a Hyperplane?

Simply put, a hyperplane is a subspace in `p-dimensional` space having `p -1` dimensions. For example, in two-dimensional space, the hyperplane will be of 1 dimension, or it will be a line. Similarly, in the case of 3 dimensions, it will be a two-dimensional plane.

In two dimensions the equation of the hyperplane are given by,

{% include math.html math_code="$\beta_0 + \beta_1X_1 + \beta_2X_2 = 0$" style="margin-top:0.2em;" %}

{% include math.html math_code="$where\ vector\ (X1,\ X2)\ is\ on\ the\ hyperplane$" %}

We can also find some similarities of this equation with the equation of a line.

It's fairly easy to extend this equation and find the equation of a hyperplane in `p` dimensions.

{% include math.html math_code="$\beta_0 + \beta_1X_1 + \beta_2X_2 + ... + \beta_pX_p = 0$" style="margin-top:0.2em;" %}

Now if,

{% include math.html math_code="$\beta_0 + \beta_1X_1 + \beta_2X_2 + ... + \beta_pX_p = 0 > 0$" style="margin-top:0.2em;" %}

Then the vector is on the one side of the hyperplane and if,

{% include math.html math_code="$\beta_0 + \beta_1X_1 + \beta_2X_2 + ... + \beta_pX_p = 0 < 0$" style="margin-top:0.2em;" %}

The vector is on the other side of the plane.

To sum it up, our main aim in case of Maximal Margin Classifier is to create a hyperplane fitted on a training data of `n X p` matrix `X`, containing `n` training observations in `p`-dimensional space such that all these vectors falls in one of the two classes divided by the hyperplane.

If we represent the classes(labels) for all the n values,

{% include math.html math_code="$y_1, ..., y_n\ \epsilon \{-1, 1\}$" style="margin-top:0.2em;" %}

Where -1 represents one class and 1 represents the other class.

Our main aim for any incoming test vector,

{% include math.html math_code="$x^* = (x_1^*\ ...\ x_p^*)^T$" style="margin-top:0.2em;" %}

is that our model has to allot this incoming test vector to one of the two classes. This equation given the class of the incoming test vector.

{% include math.html math_code="$f_x^* = \beta_0 + \beta_1x_{1}^* + \beta_2x_{2}^* + ... + \beta_px_{p}^*$" style="margin-top:0.2em;" %}

If the value of this function is positive, we assign it to class 1, otherwise, we assign it to class -1.

A simple issue in this approach is that there are infinite number of hyperplanes possible that can divide a perfect distribution.

{% include lazyload.html image_src="https://i.ibb.co/Q9X5Mdr/Screenshot-2020-04-26-at-11-50-26-PM.png" image_alt="Infinite possible hyerplanes in SVM" image_title="Infinite possible hyerplanes in SVM" %}

The problem reduces to choosing the best hyperplane possible which divides the observations into two parts.

A natural choice is to find the perpendicular distance of each observation from the potential hyperplanes, the one which produces the maximum `margin` from both the sides is chosen as the hyperplane.

{% include lazyload.html image_src="https://i.ibb.co/XYgV0Yg/Screenshot-2020-04-25-at-9-02-13-PM.png" image_alt="SVM: Choosing a hyperplane" image_title="SVM: Choosing a hyperplane" %}

Once we have the hyperplane, it is fairly easy to predict the classes of test observations.

The only assumption that we are making here is that a hyperplane dividing the observations in the training set will also divide the observations in the test set, which is not always true. Therefore, this model can lead to overfitting when `p` is large.

We have already discussed that the points on dashed line are called support vectors and it has been found that the position of hyperplane only depends on support vector and is not dependent on the other observations in the dataset.

This is how we define a Maximal margin classifier. There are a few issues with Maximal Margin Classifier.

* It doesn't work on observations where no clear hyperplane is present between different classes.
* A small addition of observation near the hyperplane can lead to a lot of change in the hyperplane making it a lot volatile.

To cope with the disadvantages of Maximal Margin classifiers, we are introduced to the concept of soft margin.

Simly put, we create a hyperplane which almost separates all of the classes, rather than surely separating all of the classes. This brings us to the concept of Support Vector Classifier.

## Support vector classifier

In case of Support vector classifiers, we allow a few observations to be on the wrong side of hyperplane making the model a little more robust to individual observation and helps us to better classify other and most of the observations.

> Support vector classifier is also known as a soft margin classifier.

The observations on the wrong side of the hyperplane are obviously misclassified by the model. But this helps to improve the overall accuracy of the model.

{% include lazyload.html image_src="https://i.ibb.co/ZdzhYrp/Screenshot-2020-04-27-at-9-48-20-PM.png" image_alt="Infinite possible hyerplanes in SVM" image_title="Infinite possible hyerplanes in SVM" %}

There is not much difference in the idea behind the generation of the model. In case of support vector classifier as well, we want to maximize the value of Margin.

{% include math.html math_code="$y_i(\beta_0 + \beta_1x_{i1} + \beta_2x_{i2} + ... + \beta_px_{ip}) \geq M(1 - \epsilon_{i})$" style="margin-top:0.2em;" %}

{% include math.html math_code="$where\ \epsilon_i \geq 0\ and\ \displaystyle \sum _{i=1}^{n} \epsilon_i \leq C$" %}

For any given observation vector on either side of plane, `epsilon`( also called a slack variable), gives the point at which it is located, relative to the hyperplane and margin.

If `i`th slack variable is on the right side of the hyperplane then the value of that variable is 0. Also, if

{% include math.html math_code="$\epsilon_i > 0$" style="margin-top:0.2em;" %}

then the point `i` is on the wrong side of the margin. But if,

{% include math.html math_code="$\epsilon_i > 1$" style="margin-top:0.2em;" %}

then the slack variable is on the wrong side of the hyperplane.

If we extend this observation to the tuning variable, `C`, we can deduce that `C` is the number which determines the count and severity of the violations to the margins and the hyperplane.

The value of `C` is considered as the tuning parameter which is generally chosen by cross-validation. `C` also controls the bias-variance trade-off for the model.

If the value of `C` is small, we allow a lesser number of observations to be on the wrong side which will fit perfectly to a data set having data with high bias and low variance and vice-versa.

Again similar to Maximal Margin Classifier, it was found that all the observations don't get to decide the position of a hyperplane of the Margin. It is only dependent on the observations on or inside the margins.

If we expand these points a little we can get to the Support Vector Machines. Let's discuss them in some detail.

## Support Vector Machines

In the Support vector Machine, we introduce another factor called the kernel, which is the result of enlarging of support vector classifiers in a specific way.

According to our discussions in support vector classifier, its equation can be re-written as,

{% include math.html math_code="$f(x) = \beta_0 +\displaystyle \sum_{i=1}^n \alpha_i<x, x_i>$" style="margin-top:0.2em;" %}

{% include math.html math_code="$where\ <x, x_i>\ is\ the\  inner\ product\ between\ the\ new\ point\ x\ and\ other\ x_i\ points$" %}

> The implementation of the inner product is hidden on purpose and we should be good without knowing the details of it.

We can directly replace all the instances of the inner product with a general term called the kernel.

{% include math.html math_code="$f(x) = \beta_0 +\displaystyle \sum_{i \epsilon S} \alpha_iK(x, x_i)$" style="margin-top:0.2em;" %}

as only support vectors are responsible for the creation of the hyperplane.

For `p` planes equation of kernel becomes,

{% include math.html math_code="$K(x_i, x_{i^`}) = (1 +\displaystyle \sum_{j=1}^p x_{ij}x{i`j} )^d$" style="margin-top:0.2em;" %}

which is known as a polynomial kernel of degree `d`. This type of model leads to much flexible decision boundary.

## Support Vector Machine for more than two classes

During the discussion for support vector machines, we haven't really talked about the case when the number of possible classifications can be more than 2.

We can solve these problems by extending the simple SVM in two ways.

* **One versus One Classification**

In this type of classification, we compare each class with another class one by one and trying to classify each incoming vector to one of the two possible classes chosen at the given instance.

Finally, for a vector, we will choose the class to which it belonged to most of the time during the training of the model.

* **One versus All Classification**

At each instance, we compare of the `K` class to the remaining `K - 1` classes. Finally, we will assign any upcoming test vector to the class which produces the highest values of the constant, or we want to maximize.

{% include math.html math_code="$\beta_0k +\beta_{1k}x_1^* +\beta_{2k}x_2^* +...+\beta_{pk}x_p^*$" style="margin-top:0.2em;" %}

## Support Vector Machine using Sklearn

Now we will try to train a Support Vector Machine model using sklearn. We are going to work on the already available cancer data which we have used in [other posts](https://ranvir.xyz/blog/beginners-guide-to-classification-decision-trees-sklearn/#classification-trees-using-sklearn) as well.

So, the idea behind the data is that, we have been given some cancer patients info, for example what is the perimeter, radius and whole lot of other stuff about the cancer. Our goal is to find whether the cancer is `WDBC-Malignant` or `WDBC-Benign`.

Let's import everything first.

```python
import pandas as pd
import numpy as np
```

Let's import the data and put in a Data Frame.

```python
from sklearn.datasets import load_breast_cancer
cancer = load_breast_cancer()

df = pd.DataFrame(cancer['data'], columns=cancer['feature_names'])
df.head()
```

{% include lazyload.html image_src="https://i.ibb.co/3ckw2d7/Screenshot-2020-05-01-at-1-56-38-AM.png" image_alt="SVM cancer dataframe head" image_title="SVM cancer dataframe head" %}

Read more about data using the following code,

```python
print(cancer['DESCR'])
```

Target values are present in other key.

```python
cancer['target']
```

Let's split the data into training and test data.

```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(df, cancer['target'], test_size=0.40)
```

Let's train the model.

```python
from sklearn.svm import SVC

model = SVC()
model.fit(X_train, y_train)
```

{% include lazyload.html image_src="https://i.ibb.co/W6jtYHY/Screenshot-2020-05-01-at-1-59-12-AM.png" image_alt="SVM default parameters" image_title="SVM default parameters" %}

You can see the default values of tuning variables is used. There are a lot of values which we can change. We will talk about them in our later posts. Please [subscribe](https://ranvir.xyz/blog/subscribe) to know when I publish that post.

Let's [evaluate the model](https://ranvir.xyz/blog/how-to-evaluate-your-machine-learning-model-like-a-pro-metrics/).

```python
from sklearn.metrics import classification_report
from sklearn.metrics import confusion_matrix

predictions = model.predict(X_test)

print(confusion_matrix(y_test, predictions))
print(classification_report(y_test, predictions))
```

{% include lazyload.html image_src="https://i.ibb.co/3cwJJ6W/Screenshot-2020-05-01-at-2-02-38-AM.png" image_alt="Confusion matrix and classification report for SVM" image_title="Confusion matrix and classification report for SVM" %}

Thats it for this version of Support Vector Machine discussion. Feel free to express your thoughts in the comments and share this post with your friends.

Resources:

1. [ISLR](https://faculty.marshall.usc.edu/gareth-james/ISL/ISLR%20Seventh%20Printing.pdf)