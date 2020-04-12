---
layout: post
title: A Beginner's guide to classification Trees using sklearn | Decision Trees
date: 2020-04-11T21:43:43.067Z
updated_date: 2020-04-11T21:43:43.090Z
description: Classification tree beginner's explanation with Gini Index,
  Entropy, Information gain and sklearn and finally discussion on metrics of
  tree.
published: true
image: https://i.ibb.co/1rhJkq4/Main-Images-1.png
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
{% include lazyload.html image_src="https://i.ibb.co/1rhJkq4/Main-Images-1.png" image_alt="Beginners guide to classification tree using sklearn" image_title="Beginners guide to classification tree using sklearn" %}

Classification Trees are the trees in which we classify the values as the output of the model.

For example, predicting that a customer is worthy of giving out the loan or not using the data of his salary and other credit history.

{% include lazyload.html image_src="https://i.ibb.co/cDS9RN7/Screenshot-2020-04-04-at-12-14-54-AM.png" image_alt="Loan Provider company decision Tree" image_title="Loan Provider company decision Tree" %}

As we already know from our previous discussion on Regression Trees, that tree algorithms are Greedy in nature which means they tend to choose the better node now, rather than choosing a node that will create a better tree later.

Also, in contrast to the regression tree model where the predicted response of any given node is the mean of all the observations in the region, in classification trees predicted response is the most commonly occurring observation in the region to which it belongs.

Read the following post for more details.

{% include linked_post.html url="guide-to-decision-regression-trees" %}

In that post, we also discussed [RSS( Residual Sum of Squares)](https://ranvir.xyz/blog/guide-to-decision-regression-trees/#prediction-using-stratification-of-feature-space) which is the value that we want to maximize while building the regression tree.

Of course, we can't use RSS in classification trees.

We have similar terms in Classification trees that we can use. We can choose either one of these. These terms are used to quantify the split that we make for choosing the feature as the node of the tree.

1. Classification Error rate
2. Entropy
3. Gini Index

## Classification Error Rate for Classification Trees

Classification Error rate is simply the fraction of the training observations in that region that do not belong to the most common class.

Mathematically,

{% include math.html math_code="$E = 1 - max(p(k))$" style="margin-top:0.2em;" %}

{% include math.html math_code="$Where\ p(k)\ is\ the\ proportion\ of\ training\ observations\ in\ the\ mth\ region\ that\ are\ from\ the\ kth\ class$" %}

Classification error rate is not used generally because it is not sensitive for tree-growing, therefore, `Entropy` or `Gini index` is used instead.

## Entropy in Classification tree

It's the measure of amount of uncertainty in the data(Randomness). Higher the uncertainty, higher is the entropy.

The value of entropy is `zero` when there is no uncertainty in some event. For example, if we are tossing a coin having heads on both sides.

Mathematically, entropy is given by

{% include math.html math_code="$H(s) =\displaystyle \sum_{x \epsilon X} p(x) log_2 \frac{1}{p(x)}$" style="margin-top:0.2em;" %}

{% include math.html math_code="$where\ p(x)\ is\ the\ proportion\ of\ occurring\ of\ some\ event$" %}

For example, for a simple coin toss, the probability is `1/2`.

## Information Gain in classification trees

This is the amount of value gained for a given set `S` when some feature `A` is selected as a node of the tree.

While selecting any node for the tree generation we want to maximize the Information Gain at that given point.

Information gain is given as the change in the Entropy before and after selecting any given feature as the node of the tree.

Mathematically, it is given as,

{% include math.html math_code="$IG(S, A) = H(s) - H(S, A)$" style="margin-top:0.2em;" %}

{% include math.html math_code="$IG(S, A) = H(s) - \displaystyle \sum_{i=0}^{n} P(x) * H(x)$" %}

{% include math.html math_code="$where\ H(S)\ is\ the\ Entropy\ of\ entire\ Set$" %}

{% include math.html math_code="$and\ \sum_{i=0}^{n} p(x) * H(x)\ is\ the\ Entropy\ after\ applying\ feature\ x\ where\ P(x)\ is\ the\ proportion\ of\ event\ x$" %}

We will discuss it further while creating the model using Information Gain.

> Information gain is the value of entropy that we removed after adding a node to the tree.

## Gini Index in Classification Trees

This is the default metric that the Sklearn classifier tends to increase. 

It is used to quantify the split made in the tree at any given moment of node selection.

Mathematically, gini index is given by,

{% include math.html math_code="$G = \displaystyle \sum_{k=1}^{K} P(k)(1 - P(k))$" style="margin-top:0.2em;" %}

{% include math.html math_code="$Where\ P(k)\ is\ the\ proportion\ of\ training\ instances\ with\ class\ k$" %}

> Minimum value that the Gini index can get is 0.

For example, A coin having heads on both sides will give Gini Index as 0.

{% include math.html math_code="$(1 * (1 - 1)) = 0$" style="margin-top:0.2em;" %}

Gini index also tells about the purity of node selection. If a node selected is very pure the value of Gini index will be less.

## Gini Gain in Classification Trees

As we have information gain in the case of entropy, we have Gini Gain in case of the Gini index.

It is the amount of Gini index we gained when a node is chosen for the decision tree.

We will take an example to understand these terms in little more detail.

Let's consider the following data source,

```
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
```

The following data contains whether we played golf when the following weather conditions were present.

Let's try to use Entropy and Gini index and try to create the first node for the Decision tree using them.

## Using Entropy and Information Gain to create Decision tree nodes

### Calculate the overall entropy

```
Total yes cases = 9
Total No cases = 5
Total Cases = 14
```

{% include math.html math_code="$\frac{9}{14}\log _{2} \frac{14}{9} + \frac{5}{14}\log _{2} \frac{14}{5}$" style="margin-top:0.2em;" %}

{% include math.html math_code="$0.940$" %}

> More the value of entropy inclined toward 1, more is the randomness in the data.

As we have already evaluated the value of total entropy, let's calculate the information gain while choosing each and every feature separately.

Let's start with the `wind` feature.

{% include math.html math_code="$IG(S, Wind) = H(S) - \sum _{i=0}^{n} P(x) * H(x)$" style="margin-top:0.2em;" %}

```
Total Weak wind cases = 8
Total Strong wind cases = 6
Total Cases = 14
```

#### Entropy for Weak wind

{% include math.html math_code="$H(S_{weak}) = \frac{6}{8} \log_{2}\frac{8}{6} + \frac{2}{8} \log_{2}\frac{8}{2}$" style="margin-top:0.2em;" %}

{% include math.html math_code="$0.811$" %}

#### Entropy for Strong wind

{% include math.html math_code="$H(S_{strong}) = \frac{3}{6} \log_{2}\frac{6}{3} + \frac{3}{6} \log_{2}\frac{6}{3}$" style="margin-top:0.2em;" %}

{% include math.html math_code="$1.00$" %}

Total Information Gain can be calculated as follows,

{% include math.html math_code="$IG(S, Wind) = H(S) - P(S_{weak}) * H(S_{weak}) - P(S_{strong}) * H(S_{strong})}$" style="margin-top:0.2em;" %}

{% include math.html math_code="$0.940 - \frac {8}{14} (0.811) - \frac{6}{14}(1.00)$" %}

{% include math.html math_code="$0.048$" %}

Similarly, we will calculate `IG` for other features as well and select the one which produces the highest value of `IG`.

We will continue this process until leaf nodes are reached for every branch created.

## Using Gini Index and Gini Gain to create Decision tree nodes

### Calculate the overall Gini impurity

```
Total yes cases = 9
Total No cases = 5
Total Cases = 14
```

{% include math.html math_code="$GI(S) = \frac{9}{14}(1 - \frac{9}{14}) + \frac{5}{14}(1 - \frac{5}{14})$" style="margin-top:0.2em;" %}

{% include math.html math_code="$0.46$" %}

As we have already evaluated the value of total Gini impurity, let's calculate the Gini gain while choosing each and every feature separately.

Let's start with the `wind` feature.

```
Total Weak wind cases = 8
Total Strong wind cases = 6
Total Cases = 14
```

#### Gini Index for Weak wind

{% include math.html math_code="$GI(S_{weak}) = \frac{6}{8}(1 - \frac{6}{8}) + \frac{2}{8}(1 - \frac{2}{8})$" style="margin-top:0.2em;" %}

{% include math.html math_code="$\frac{3}{8}$" %}

#### Gini Index for Strong wind

{% include math.html math_code="$GI(S_{Strong}) = \frac{3}{6}(1 - \frac{3}{6}) + \frac{3}{6}(1 - \frac{3}{6})$" style="margin-top:0.2em;" %}

{% include math.html math_code="$\frac{1}{2}$" %}

Total Gini Gain can be calculated as follows,

{% include math.html math_code="$GG(S_{wind}) = GI(S) - \frac{8}{14} * GI(S_{weak}) - \frac{6}{14} * GI(S_{strong})$" style="margin-top:0.2em;" %}

{% include math.html math_code="$GG(S_{wind}) = 0.46 - 0.214 - 0.214$" %}

{% include math.html math_code="$0.0314$" %}

Similarly, we will calculate `GG` for other features as well and select the one which produces the highest value of `GG`.

This is the basic understanding of Classification Trees.

## Classification Trees using Sklearn

We will be using sklearn to train a model of breast cancer data.

### Import everything

```python
import matplotlib.pyplot as plt

from sklearn.model_selection import train_test_split
from sklearn.datasets import load_breast_cancer
from sklearn.metrics import classification_report, confusion_matrix
from sklearn.tree import DecisionTreeClassifier

%matplotlib inline
```

### Load data and split into training and testing data

```python
X, y = load_breast_cancer(return_X_y=True)

X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=0)
```

### Initialize the model with default criterion (Gini Index)

```python
clf = DecisionTreeClassifier()
clf.fit(X_train, y_train)
```

{% include lazyload.html image_src="https://i.ibb.co/NCkpMQQ/Screenshot-2020-04-13-at-1-20-07-AM.png" image_alt="Classification tree Using gini index" image_title="Classification tree Using gini index" %}

### Predict the model and check the Reports

```python
predictions = clf.predict(X_test)

print(confusion_matrix(y_test, predictions))
print(classification_report(y_test, predictions))
```

{% include lazyload.html image_src="https://i.ibb.co/xH5JjMx/Screenshot-2020-04-13-at-1-28-15-AM.png" image_alt="Classification tree Using gini index metrics" image_title="Classification tree Using gini index metrics" %}

### Using Entropy as the criterion for predicting classification Model

```python
clf_entropy = DecisionTreeClassifier(criterion='entropy')
clf_entropy.fit(X_train, y_train)
predictions_entropy = clf_entropy.predict(X_test)
print(confusion_matrix(y_test, predictions_entropy))
print(classification_report(y_test, predictions_entropy))
```

{% include lazyload.html image_src="https://i.ibb.co/8m7g9xd/Screenshot-2020-04-13-at-1-28-25-AM.png" image_alt="Classification tree Using entropy metrics" image_title="Classification tree Using entropy metrics" %}

As you can see Entropy performed better in this case. But it really depends upon you which you want to choose.

Thanks for reading and do [subscribe](https://ranvir.xyz/blog/subscribe) for more such posts.