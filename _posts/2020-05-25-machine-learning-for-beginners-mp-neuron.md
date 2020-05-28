---
layout: post
title: Machine learning for beginners - MP Neuron
date: 2020-05-25T18:24:54.259Z
updated_date: 2020-05-25T18:24:54.280Z
published: false
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

Some people refer `g(x)` as the activation function and `f(x)` as the loss function.

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

- Talk about the line, some mathematical equations will also work.
- Tell how on one side the value is greater than 0 and on other side it is less than 0.

## Epochs

## Learning Rate

## The MP neuron class itself

## Training a simple model with plots

## Animation plot of learning.

## No Disadvantage discussion in this post