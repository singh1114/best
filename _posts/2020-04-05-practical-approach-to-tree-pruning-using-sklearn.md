---
layout: post
title: A practical approach to Tree Pruning using sklearn
date: 2020-04-05T14:32:51.943Z
updated_date: 2020-04-05T14:32:51.958Z
description: >-
  Tree pruning and finding prune subtree using cost complexity pruning or and
  finding optimal alpha value using sklearn 
published: true
image: 'https://i.ibb.co/XWMPn8d/Main-Images-2-1.png'
tags:
  - machinelearning
  - sklearn
  - python
  - datascience
categories:
  - machinelearning
  - sklearn
  - python
  - datascience
include_mathjax: true
---
{% include lazyload.html image_src="https://i.ibb.co/XWMPn8d/Main-Images-2-1.png" image_alt="Practical approach to tree pruning using sklearn" image_title="Practical approach to tree pruning using sklearn" %}

As we have already discussed in the [regression tree post](https://ranvir.xyz/blog/guide-to-decision-regression-trees/) that simple tree prediction can lead to a model which overfits the data and produce bad results with the test data. Tree Pruning is the way to reduce the overfitting by creating smaller trees.

Tree Pruning isn't only used for regression trees. We also make use of it in the [classification trees](https://ranvir.xyz/blog/decision-tree-algorithms-machine-learning/#classification-trees) as well.

As the word itself suggests, the process involves cutting the tree into smaller parts.

We can do pruning in two ways.

## Pre-pruning or early stopping

This means stopping before the full tree is even created. The idea is to build the tree only as long as the decrease in the `RSS` due to each split exceeds some threshold.

This means that we can stop further creating of the tree as soon as the `RSS` decrease while producing the next node is lower than the given threshold.

This might lead to some shortsightedness as there might be some cases in which there might a large reduction in the `RSS` at the later ends of the tree creation.

Thus, we try to make use of much more complex post pruning.

## Post Pruning

In Post pruning we grow a large tree `T0`, and then prune it back in order to obtain a subtree such that we get the lowest test error rate.

Now, the problem with this algorithm is that, we don't want to go to every subtree and choose each one of them to calculate the change in the test error rate.

**Cost complexity Pruning** or **Weakest link Pruning** helps us with that. It introduces a new term, `alpha`. We pick only those trees which are indexed by this `alpha`.

{% include math.html math_code="$\alpha = alpha\ $" style="margin-top:0.2em;" %}

For each value of `alpha` we have a subtree which can minimize the value of

{% include math.html math_code="$\displaystyle \sum_{m=1}^{\left | T \right |} \sum_{i:x_i \epsilon R_m} (y_i - \widehat{y}_{R_m})^ {2} + \alpha\left | T \right |$" style="margin-top:0.2em;" %}

{% include math.html math_code="$R_m\ is\ the\ rectangle\ corresponding\ to\ mth\ terminal\ node$" %}

{% include math.html math_code="$\widehat{y}_{R_m}\ is\ the\ mean\ of\ training\ observations\ in\ R_m$" %}

## Steps involved in building Regression Tree using Tree Pruning

* Split the data to grow the large tree stopping only when the terminal node contains fewer than some minimum number of observations. For example, we will keep dividing until each region has less than 20 data points.

* Apply cost complexity pruning to the large tree and get the sequence of best subtrees as a function of `alpha`. The idea is to minimize the cost-complexity function.

{% include math.html math_code="$C_\alpha(T) = R(T) + \alpha \left | T \right |$" style="margin-top:0.2em;" %}

{% include math.html math_code="$where\ T\ is\ the\ number\ of\ leaves\ of\ the\ tree$" %}

{% include math.html math_code="$and\ R(T)\ is\ the\ loss\ function\ calculated\ across\ the\ leaves.$" %}

* Use K-Fold cross-validation to choose `alpha`. Simply putting, divide the training data into `K` smaller parts and run the `fit` function on `K` iterations with leaving `K` different subsets of training data as validation data and finally calculate the Mean Square Error using these K validation subsets as a function of `alpha`. (Will discuss k-fold cross validation in feature engineering post.)

* Pick the `alpha` value with minimum average error.

* Return the subtree that corresponds to the chosen value of `alpha`.

## Using sklearn to see pruning effect on trees

We will use simple data to check the effect of pruning on the Decision Tree. Let's first get the data and split it accordingly.

```python
import matplotlib.pyplot as plt

from sklearn.model_selection import train_test_split
from sklearn.datasets import load_breast_cancer
from sklearn.tree import DecisionTreeClassifier

X, y = load_breast_cancer(return_X_y=True)
X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=0)
```

To get the different applicable `alpha` values and corresponding impurity in the leaf nodes introduced due to that, we can use the `cost_complexity_pruning_path` function present in the `DecisionTreeClassifier` class.

```python
clf = DecisionTreeClassifier()
path = clf.cost_complexity_pruning_path(X_train, y_train)
path
```

This gives,

```json
{'ccp_alphas': array([0.        , 0.00226647, 0.00464743, 0.0046598 , 0.0056338 ,
        0.00704225, 0.00784194, 0.00911402, 0.01144366, 0.018988  ,
        0.02314163, 0.03422475, 0.32729844]),
 'impurities': array([0.        , 0.00453294, 0.01847522, 0.02313502, 0.02876883,
        0.03581108, 0.04365302, 0.05276704, 0.0642107 , 0.0831987 ,
        0.10634033, 0.14056508, 0.46786352])}
```

This contain two [Numpy Arrays](https://ranvir.xyz/blog/data-science-i-all-things-you-need-to-know-about-numpy/) of `alpha` and `impurities`.

We can plot this on graph to see the relation. 

```python
ccp_alphas, impurities = path.ccp_alphas, path.impurities

plt.figure(figsize=(10, 6))
plt.plot(ccp_alphas, impurities)
plt.xlabel("effective alpha")
plt.ylabel("total impurity of leaves")
```
{% include lazyload.html image_src="https://i.ibb.co/1Lzdc67/Screenshot-2020-04-05-at-7-45-52-PM.png" image_alt="Alpha relation with leaves impurity" image_title="Alpha relation with leaves impurity" %}

Finding an optimal value of alpha using Python

```python
clfs = []

for ccp_alpha in ccp_alphas:
    clf = DecisionTreeClassifier(random_state=0, ccp_alpha=ccp_alpha)
    clf.fit(X_train, y_train)
    clfs.append(clf)
```

As we already know that there is a strong relation between, alpha and the depth of the tree. We can find the relation using this plot.

```python
tree_depths = [clf.tree_.max_depth for clf in clfs]
plt.figure(figsize=(10,  6))
plt.plot(ccp_alphas[:-1], tree_depths[:-1])
plt.xlabel("effective alpha")
plt.ylabel("total depth")
```

{% include lazyload.html image_src="https://i.ibb.co/4tDdcXj/Screenshot-2020-04-05-at-7-50-27-PM.png" image_alt="Alpha relation with depth of tree" image_title="Alpha relation with depth of tree" %}

Use the following code to find the relation between `alpha` and accuracy.

```python
from sklearn.metrics import accuracy_score

acc_scores = [accuracy_score(y_test, clf.predict(X_test)) for clf in clfs]

tree_depths = [clf.tree_.max_depth for clf in clfs]
plt.figure(figsize=(10,  6))
plt.grid()
plt.plot(ccp_alphas[:-1], acc_scores[:-1])
plt.xlabel("effective alpha")
plt.ylabel("Accuracy scores")
```

{% include lazyload.html image_src="https://i.ibb.co/FKn78xT/Screenshot-2020-04-05-at-7-50-15-PM.png" image_alt="Alpha relation with accuracy of tree" image_title="Alpha relation with accuracy of tree" %}

Please share on social media and [subscribe to the newsletter](https://ranvir.xyz/blog/subscribe) to read more such posts.