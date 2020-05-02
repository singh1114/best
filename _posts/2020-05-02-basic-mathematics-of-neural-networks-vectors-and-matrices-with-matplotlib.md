---
layout: post
title: Basic Mathematics of Neural Networks | Vectors and Matrices with Matplotlib
date: 2020-05-02T14:29:31.226Z
updated_date: 2020-05-02T14:29:31.242Z
published: false
show_ads: false
include_mathjax: true
---
Vector and Matrices are at the heart of all Neural Networks. Today we are going to learn about vector and Matrix mathematics with the help of `Matplotlib`.

First, we are going to understand different analogies in Neural Networks which correspond to Vectors and Matrices.

## Vector in Machine Learning

> A vector represent one of the data point of the whole dataset.

For example, let's say you are working with a YouTube video creator who make unboxing videos of different phones and other electronic stuff.

Just for the simplicity, your task is to predict which phone to review next so that your channel can get maximum views and maximum social media shares.

You already have the historical data of the channel. You also have a list of 50 upcoming phones but you are only allowed to review 5 out of them.

The features available to you are:

```
| Company  | Price | Number of Cameras | Screen length | Traction |
|----------|-------|-------------------|---------------|----------|
| Apple    | 1000  | 3                 | 5.5           | 85%      |
```

This one data point can be called as a vector with number of features being the dimension of the plane in which this vector can be represented.

## Matrix representation in Machine Learning

> A Matrix can be represented as a set of a few vectors. The collection of data points can be considered as a Matrix.

For example, a few data points for predicting the next phone to review.

```
| Company  | Price | Number of Cameras | Screen length | Traction |
|----------|-------|-------------------|---------------|----------|
| Apple    | 1000  | 3                 | 5.5           | 85%      |
| Samsung  | 800   | 1                 | 6             | 70%      |
```

## Vectors in Simple Mathematics and its operations

In general, a vector is defined as something having both magnitude and direction. If we can plot this in the 2-D graph, it will be represented as a line pointing toward a direction.

From now on, we will be talking about vectors in 2-D planes to make things simple.

In mathematics, vector is represented as,

{% include math.html math_code="$\overrightarrow{x}$" style="margin-top:0.2em;" %}

Let's represent a simple vector in 2-D plane using matplotlib and numpy.

```
0, 0, 5, 3
```

{% include math.html math_code="$\begin{vmatrix}0\\ 0\end{vmatrix}\ and\ \begin{vmatrix}5\\ 3\end{vmatrix}$" style="margin-top:0.2em;" %}

### Import required packages

```python
import numpy as np
import matplotlib.pyplot as plt
```

We are going to use Matplotlib's `quiver` method to plot the vector on the 2D plane.

```python
plt.quiver(0, 0, 5, 3,  scale_units='xy', angles='xy', scale=1, color="red")

# Just to make the 
plt.xlim(-5, 10)
plt.ylim(-5, 10)
```

Let's write a function that can help us to plot vectors whenever we want to,

```python
def plot_2D_vectors(vectors, colors=('red', 'blue', 'green')):
    # random numbers
    min_x = 0
    max_x = 0
    min_y = 0
    max_y = 0
    i = -1
    for points in vectors:    
        for a in range(0, 4):
            if a % 2 == 0:
                if points[a] <= min_x:
                    min_x = points[a] - 1
                if points[a] >= max_x:
                    max_x = points[a] + 1
            else:
                if points[a] <= min_y:
                    min_y = points[a] - 1
                if points[a] >= max_y:
                    max_y = points[a] + 1
        i = i + 1
        plt.quiver(points[0], points[1], points[2], points[3], scale_units='xy', angles='xy', scale=1, color=colors[i])
    plt.xlim(min_x, max_x)
    plt.ylim(min_y, max_y)
```

This function takes two arguments, first is the vectors and other is the colors, whose default value is red, blue and green. We are also trying to figure out what should be the boundary of the graph by running a loop to find minimum and maximum of the graph by subtracting 1 from the minimum and maximum values of x and y.

This function will help us to apply various mathematical operations on vectors.

## Addition and Subtraction of Vectors

Before doing any operation on vectors, we will have to represent them using [Numpy](https://ranvir.xyz/blog/data-science-i-all-things-you-need-to-know-about-numpy/).

```python
np_vector_1 = np.array([0, 0, 5, 3])
np_vector_2 = np.array([0, 0, 6, 8])

plot_2D_vectors([np_vector_1, np_vector_2])
```

Now, let's add these two vectors and plot the new result vector.

```python
np_vector_3 = np_vector_1 + np_vector_2

plot_2D_vector(np_vector_1)
plot_2D_vector(np_vector_2, 'b')
plot_2D_vector(np_vector_3, 'g')
```

If we add two vector having obtuse angle in between them then the magnitude of the resultant vector decreases.

```python
np_vector_1 = np.array([0, 0, -5, -3])
np_vector_2 = np.array([0, 0, 6, 8])
np_vector_3 = np_vector_1 + np_vector_2

plot_2D_vectors((np_vector_1, np_vector_2, np_vector_3), ['r', 'b', 'g'])
```

Subtraction is also similar, we can plot the subtracted vector simply using the function.

```python
np_vector_1 = np.array([0, 0, -5, -3])
np_vector_2 = np.array([0, 0, 6, 8])
np_vector_3 = np_vector_2 - np_vector_1

plot_2D_vectors((np_vector_1, np_vector_2, np_vector_3), ['r', 'b', 'g'])
```

## Dot product of two vectors

Dot product of two vectors gives just the magnitude by multiplying the point-wise values in the vector.

```python
np.dot(np.array([3, 4]), np.array([5, -1]))
```

Mathematically, it is given by,

{% include math.html math_code="$\overrightarrow{x} . \overrightarrow{y} = x_i y_i + x_j y_j$" style="margin-top:0.2em;" %}

## Projection of a vector onto another vector

Projection of a vector onto another vector is the image that it makes when the vector image is seen when there is a light source right at the top of the vector whose projection is being calculated.

```python
np_vector_1 = np.asarray([0, 0, 3, 4])
np_vector_2 = np.asarray([0, 0, 4, -1])
dot_product = np.dot(np_vector_1, np_vector_2)
proj_vector = (dot_product/np.power(np.linalg.norm(np_vector_2), 2))*np_vector_2

plot_2D_vectors((np_vector_1, np_vector_2, proj_vector), ['r', 'green', 'red'])
```

Projection of vector having 90 degree between them is 0.

```python
np_vector_1 = np.array([0, 0, 4, 0])
np_vector_2 = np.array([0, 0, 0, 4])
dot_product = np.dot(np_vector_1, np_vector_2)
proj_vector = (dot_product/np.power(np.linalg.norm(np_vector_2), 2))*np_vector_2

plot_2D_vectors((np_vector_1, np_vector_2, proj_vector), ['r', 'green', 'red'])
```

Mathematically, projection of one vector on another is given by,

{% include math.html math_code="$\frac{\overrightarrow{x} . \overrightarrow{y}}{\begin{Vmatrix}\overrightarrow{y}\end{Vmatrix}^2}\ \overrightarrow{y}$" style="margin-top:0.2em;" %}

## Matrices in Mathematics

Matrices are the collection of vectors.

Mathematically they are represented as,

\begin{vmatrix}x_1 & x_2 & x_3\\ x_4 & x_5 & x_6\\ x_7 & x_8 & x_9\end{vmatrix}

## Matrix Multiplication.

Matrix multiplication is done by multiplying and adding every row to the corresponding columns.

Read the [following post](http://www.texample.net/tikz/examples/matrix-multiplication/) to understand it thoroughly.

We can do the same using numpy dot product as well.

```python
vector_1 = np.array([(1, 2, 3), (4, 5, 6), (7, 8, 9)])
vector_2 = np.array([(1, 4), (2, 5), (3, 6)])

vector_1.dot(vector_2)

> array([[ 14,  32],
       [ 32,  77],
       [ 50, 122]])
```

That's it for the basic version of mathematics using `numpy` and `matplotlib`. We will talk about more extended version of mathematics in different models in later versions.

Do [subscribe](https://ranvir.xyz/blog/subscribe) 