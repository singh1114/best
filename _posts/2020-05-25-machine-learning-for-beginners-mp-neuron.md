---
layout: post
title: Machine learning for beginners - MP Neuron
date: 2020-05-25T18:24:54.259Z
updated_date: 2020-05-25T18:24:54.280Z
description: Introduction to Neural Networks using MP neuron with full
  discussion on different things like threshold, loss function and learning
  algorithm.
published: true
tags:
  - machinelearning
  - datascience
  - numpy
categories:
  - machinelearning
  - datascience
  - numpy
show_ads: false
---
MP neuron is the first step toward opening up the doors of artificial neural networks, which was made somewhat by copying some parts of biological neural networks.

A lot of posts do a wonderful job in explaining the biological neural network. So, I am not going to step into that territory. What we are going to in this post is build the intuition for upcoming posts of more sophisticated neural networks by learning how it all started.

We are going to talk about things like, how MP neuron works. We will also, build the MP neuron class which we can use to train our models and predict simple things.

So, Let's get started.

First, those who are interested in knowing the workings of biological neural network can check it on [WikiPedia](https://en.wikipedia.org/wiki/Biological_neuron_model).

Let's get back to the example that we used in the case of our [Mathematics for Neural Network post](https://ranvir.xyz/blog/neural-networks_maths-vectors-matrices-matplotlib-numpy/).

> Let’s say you are working with a YouTube video creator who makes unboxing videos of different phones and other electronic stuff. Your task is to predict which phone to review next so that your channel can get maximum views and maximum social media shares.

Now there are a lot of ways in which we can tackle this problem. We can go with a rule based system where we define which brands we want to review, what phone cost we want to review and many more.

The YouTube channel owner interviewed someone for his last YouTube video and told him that the MP neuron is the best way to make such predictions, and he should definitely ask his Data scientist to use MP neuron.

You tried to tell him about stuff like accuracy and other things, but he refuses to listen. So, you decided to show him by explaining him about the inner working of the neuron.

Let's take an example of the data that you had available and try building the intuition from there.

```
| Company  | Price | Number of Cameras | Screen length | Reviewed |
|----------|-------|-------------------|---------------|----------|
| Apple    | 1000  | 3                 | 5.5           |   1      |
| Samsung  | 800   | 1                 | 6             |   0      |
```

`Reviewed` is target value that we want to predict.

## Building blocks of a Neural Network

In case of every Neural Network, we have a simple job, we will feed the data to the neuron and it will give us some output. For example, telling us whether we should review the phone or not.

This inner algorithm which helps a neuron to come to a conclusion is known as the `Model`.

Visually, if we consider only two input variables(for example `Company` and `Price`), it will look like,

{% include lazyload.html image_src="https://i.ibb.co/Y3pQztv/Screenshot-2020-05-26-at-12-49-48-AM.png" image_alt="MP neuron" image_title="MP neuron" %}

Don't get confused by the `f(g(x))`, it's really simple.

`g(x)` stands for adding the input variables together on the other hand, `f` has this simple definition.

```
f(g(x)) is 1, if g(x) >= b
       and 0, if g(x) < b
```

This simply means that we are going to sum all the input variables, and if the sum of those variables is greater than or equal to some variable, `b`, we will return 1( or we will review the phone) else it will return 0( We will not review).

## Threshold in Neural Network

Wait, did I forgot to define, `b`. Sorry, my bad. `b` is term that we want to find so that we can find a clear separation between our classes( Reviewed and Not Reviewed in this case).

> What are we going to do about the features having String values?

You might be asking yourself if we are going to sum stuff together, we won't be able to use String features like, `Company` etc, right?

Well it is partially true.

Of course, we can't use it directly, but we can convert this column into few different columns like, `is_apple` or `is_samsung` which will tell whether the phone was of Company `Apple` or not and whether the phone was of Company `Samsung` or not.

We can easily do this using Pandas,

```python
pd.get_dummies(training_dataFrame(['Company']))
```

Therefore, we will end up having `k` different columns, if we have `k` different classes in the column.

If you don't understand Pandas stuff, you might want to quickly, get a sneak peek using my post on Pandas( Self promotion never hurts).

{% include linked_post.html url="data-science-ii-introduction-to-pandas" %}

## Binary Data

Well, you might have guessed it till now and if you haven't, we can only use features having binary data. If we don't have binary features, we will have to convert it to Binary features.

For example, We can change `Cost` feature to `Cost above > $1000` etc.

## Geometrical representation

Geometrically MP neuron is not very different from the [Support Vector Machine](https://ranvir.xyz/blog/svm-support-vector-machines-in-machine-learning/) model which also tries to divide the data using a line. The only thing missing in MP neurons is the Support Vectors.

The equation of the line is given by,

{% include math.html math_code="$x_1 + x_2 + b = 0$" style="margin-top:0.2em;" %}

This means that any point toward the one side of the line will produce +ve values and points on the other side will produce -ve values.

Extending it to the Reviewed/ Not Reviewed format, we will have all reviewed phones on one side of the line and not reviewed phones on the other.

## How to calculate the threshold?

The main purpose of any model is to learn the correct values of these variables. `b` is the only variable in MP Neuron case. We will use a small trick so that we don't have to check every possible value in the world to compute the correct threshold.

Every model is evaluated by comparing the true output with the predicted output to check how much accurate is our model. Mean Squared Error is one of those methods, which is also known as the **loss function**.

{% include math.html math_code="$\sum_{i}^{n}(y - \widehat{y})^2$" style="margin-top:0.2em;" %}

{% include math.html math_code="$where\ \widehat{y}\ is\ the\ predicted\ value.$" %}

What we want to do is to minimize the value of the loss function.

We also are aware that maximum sum that the model can have is equal to the number of features. Therefore, the value of threshold can vary from 0 to `n`.

We will calculate the corresponding loss at each data point and pick the threshold having the least loss.

## The MP neuron class itself

Now we will build the MP Neuron class that we can use to train our model. We will use the same format we were using before. A method called `fit` to fit the model and `predict` to predict the output.

```python
import pandas as pd

import numpy as np
from sklearn.metrics import accuracy_score
import operator

class MPModel:
    def __init__(self, function='sum'):
        # We can pass some initial value of threshold.
        self.threshold = None
        if function == 'sum':
            self.function = self.sum_function
        elif function == 'and':
            self.function = self.and_function
        elif function == 'or':
            self.function = self.or_function    
            
    def sum_function(self, x):
        return sum(x) >= self.threshold
    
    def and_function(self, x):
        return all(x)
    
    def or_function(self, x):
        return any(x)

    def fit(self, X_DataFrame, y_DataFrame):
        threshold_accuracy_dict = {}
        for threshold in range(len(X_DataFrame.columns) + 1):
            threshold_accuracy_dict[threshold] = None
        for threshold in threshold_accuracy_dict.keys():
            self.threshold = threshold
            predictions = self.predict(X_DataFrame)
            threshold_accuracy_dict[threshold] = accuracy_score(y_DataFrame, predictions)
        self.threshold = max(threshold_accuracy_dict.items(), key=operator.itemgetter(1))[0]
        print(self.threshold, 'threshold', threshold_accuracy_dict)

    def predict(self, X_DataFrame):
        results = np.array([])
        for i in range(len(X_DataFrame)):
            result = self.function(X_DataFrame.iloc[i])
            results = np.append(results, result)
        return results
```

## Training and predict a simple model

Consider the following data which we can use to train the MP Neuron model.

```python
df_dict = {
    'Wind': [0, 1, 0, 0, 0, 1, 1, 0, 0, 0, 1, 1, 0, 0],
    'Temp': [1, 1, 1, 0, 0, 0, 1, 0, 0, 1, 0, 0, 1, 0],
    'Played': [0, 1, 1, 0, 0, 1, 0, 0, 0, 1, 1, 1, 1, 0]
}
pd_df = pd.DataFrame(df_dict)


mpm = MPModel()
mpm.fit(pd_df[['Wind', 'Temp']], pd_df['Played'])

df_dict_test = {
    'Wind': [0, 1, 0, 0, 0],
    'Temp': [1, 1, 1, 1, 0],
    'Played': [0, 1, 1, 1, 0]
}

pd_df_test = pd.DataFrame(df_dict_test)
predictions = mpm.predict(pd_df_test[['Wind', 'Temp']])
accuracy_score(predictions, pd_df_test['Played'])
```

```python
> 0.8
```

---

We will not discuss anything related to what disadvantages does MP neuron have. We have moved the discussion to the next Neural Network in the list, which is a little better than this one.

In the second post, it will become clear to your partner that MP neuron is indeed not a good idea for the kind of problem you are trying to solve.

The reason we discussed MP Neuron is very important, It is very important to start from basics if you want to learn something. This is the model from which everything started making much more sense.