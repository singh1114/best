---
layout: post
title: Mystery of Mutable Default Arguments in Python
date: 2020-04-08T18:35:25.076Z
updated_date: 2020-04-08T18:35:25.093Z
description: Mystery of Mutable Default Arguments in Python, How not to pass
  default arguments in Python and how to handle them properly?
published: true
image: https://i.ibb.co/vxsfmtq/Main-Images-3-1.png
tags:
  - python
  - productivity
categories:
  - python
  - productivity
author_name: Prashant Sharma
author_username: sharma_pacific
show_ads: false
canonical_url: https://sharmapacific.in/mutable-default-arguments-in-python/
---
{% include lazyload.html image_src="https://i.ibb.co/vxsfmtq/Main-Images-3-1.png" image_alt="Mystery of Mutable Default Arguments in Python" image_title="Mystery of Mutable Default Arguments in Python" %}

Objects of built-in types like (`int`, `float`, `bool`, `str`, `tuple`, `Unicode`) are immutable. Objects of built-in types like (`list`, `set`, `dict`) are mutable.
A mutable object can change its state or contents and immutable objects cannot.

This is a very simple definition of a Mutable and Immutable object in Python. Now coming to the interesting part which is Mutable Default Object in function definitions.

I have written a very simple function as below -

```python
def foobar(element, data=[]):
    data.append(element)
    return data
```

In the above function, I set `data` to a list(Mutable object) as a default argument. Now let's execute this function -

```python
>>> print(foobar(12))
[12]
```

The output is as expected, Now execute multiple times -

```python
>>> print(foobar(22))
[12, 22]
>>> print(foobar(32))
[12, 22, 32]
```

{% include lazyload.html image_src="https://i.ibb.co/FK7d4XF/Screenshot-2020-04-09-at-1-19-47-AM.png" image_alt="Mutable default List in python" image_title="Mutable default List in python" %}

What is going on here? As you can see, the first time, the function returns exactly what we expected. On the second and all subsequent passes the same list is used in each call.

## Why is this happening?

Python’s default arguments are evaluated once when the function is defined, not each time the function is called. When Python encounters it, the first thing it will do is compile it in order to create a code object for this function. While this compilation step is done, Python evaluates and then stores the default arguments in the function object itself.

So, let's do some introspection, to clear the confusions, I have taken a few lines of code as below-

* Function Before Execution -

```python
def foo(l=[]):
    l.append(10)
```

After function executes this definition, You can check the default attribute for this function. by using `__defaults__`.

**About `__defaults__`:** A tuple containing default argument values for those arguments that have defaults, or None if no arguments have a default value.

```python
>>> foo.__defaults__
([],)
```

The result an empty list as the only entry in `__defaults__`

* Function After Execution-

Let's now execute this function and check the defaults.

```python
>>> foo()
>>> foo.__defaults__
([10],)
```

Astonished? The value inside the object changes, Consecutive calls to the function will now simply append to that embedded list object:

Let's execute the function multiple times:

```python
>>> foo()
>>> foo()
>>> foo()

>>> foo.__defaults__
([10, 10, 10, 10],)
```

The reason why this is happening because default argument values are stored in the function object, not in the code object (because they represent values calculated at run-time).

## The Solution

Now, the question is how to code `foobar` in order to get the behavior that we expected.

Fortunately, the solution is straightforward. The mutable objects used as defaults are replaced by None, and then the arguments are tested for None.

```python
def foobar(element, data=None):
    if data is None:
        data = []
    data.append(element)
    return data

>>> foobar(12)
[12]
```

So, by replacing mutable default arguments with None solved our problem.

## Good Use of Mutable Default Argument

However, Mutable Default Argument have some good use-case also as following-

* Binding local variable to the current value of the outer variable in a callback

* Cache/Memoization

I hope you like the explanation of Mutable Default Arguments in Python. Still, if any doubt or improvement regarding it, ask in the comment section.

References:

[Datamodel: The standard type hierarchy](https://docs.python.org/3/reference/datamodel.html#the-standard-type-hierarchy)