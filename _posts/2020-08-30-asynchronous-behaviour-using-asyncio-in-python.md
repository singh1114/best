---
layout: post
title: Asynchronous behaviour using asyncio in Python
date: 2020-08-30T13:34:22.747Z
updated_date: 2020-08-30T13:34:22.766Z
description: Asyncio helps you to write asynchronous functions using python
  making your application a lot faster with better user experience with its easy
  to use syntax.
published: true
tags:
  - python
  - django
categories:
  - python
  - django
show_ads: false
show_telegram_signup: true
---
A lot has changed since I last published my post on handling long-running async tasks in Python using celery. Last time we used it to run a few async tasks to fetch data from some service which took more than 5 minutes. You can read more about it in the post below.

{% include linked_post.html url="using-celery-to-run-long-running-task-asynchronously" %}

Although I will still use celery for these types of long-running tasks, there is a subset of tasks that are better handled inside the execution thread itself. Today we will discuss a way of handling such operations.

To the people who know me, I have started working on Node.js over a year now and have been working on it since then. During my time working on Node.js and building APIs using it, I have started loving the way in which we can handle Async behavior and long-running tasks.

{% include linked_post.html url="basic-introduction-to-node.js-async-await" %}

The idea is simple, if the task is taking more than usual time, we will run it asynchronously. Only the part that needs it, will wait for it.

I wanted to use the same concept in Python. Fortunately, in Python version `3.4`, they have introduced `asyncio` for the same purpose. In this post, we are going to talk a little about it and try to understand its importance.

By the end of the post, you will be able to understand the importance of async functions and will be able to start using them into your codebase.

## Prerequisite

I am using `Python 3.8` for this tutorial and you might want to use the same to run and try out the examples. You can try them [online as well](https://www.python.org/shell/).

## Basic async function in Python

This is how we write a basic async function in Python. 

```python
import asyncio

async def func1(a):
    print("started func 1: {}", a + 1)
    await asyncio.sleep(1)
    return a + 1

asyncio.run(func1(1))
```

**Response**

```python
started func 1: 2
2
```

You have to start by importing the `asyncio` module.

Async functions are defined just like a normal function, you just have to add the keyword, `async`. If you want to wait for the execution of some [coroutine](https://docs.python.org/3/library/asyncio-task.html#coroutines), you have to use the keyword, `await`.

Finally, you can run the function using `asyncio.run` method.

> Anytime you use the await keyword inside the async function, the thread will not move forward until we get a response from the called function.

This simple implementation will not help you understand the advantage of using async functions. In the next section, we will talk about the time taken for the execution and there you will really start to see the difference.

## Time taken for the full execution

To understand the benefits of using `async` functions, we will compare the time taken to run the same code in `async` and `sync` behavior.

Let's first write the async code.

```python
import asyncio
import time
start = time.time()


async def async_sleep():
    await asyncio.sleep(1)
    

async def func1(a):
    print("started func 1: {}", a + 1)
    await async_sleep()
    return a + 1


async def func2(a):
    print("started func 2: {}", a + 2)
    await async_sleep()
    return a + 2


async def func3(a):
    print("started func 3: {}", a + 3)
    await async_sleep()
    return a + 3


async def func4(a):
    print("started func 4: {}", a + 4)
    await async_sleep()
    return a + 4


async def main():
    tasks = (func1(1), func2(1), func3(1), func4(1))
    await asyncio.gather(*tasks)
    print("Completed after: {}", time.time() - start)

asyncio.run(main())
```

I have defined 4 different functions doing almost the same thing. Let's assume there is a long-running function called `async_sleep` which is doing some IO operation.

`asyncio.gather` is used to run the tasks passed to it concurrently.

The response after running this code is as follows.

```python
started func 1: 2
started func 2: 3
started func 3: 4
started func 4: 5
Completed after: 1.1852593421936035
```

The function completes the execution somewhere between 1-2 seconds.

Now let's try to run the `sync` version of the same code.

```python
import time
start = time.time()


def sync_sleep():
    time.sleep(1)


def func1(a):
    print("started func 1: {}".format(a + 1))
    sync_sleep()
    return a + 1


def func2(a):
    print("started func 2: {}".format(a + 2))
    sync_sleep()
    return a + 2


def func3(a):
    print("started func 3: {}".format(a + 3))
    sync_sleep()
    return a + 3


def func4(a):
    print("started func 4: {}".format(a + 4))
    sync_sleep()
    return a + 4


def main():
    func1(1)
    func2(1)
    func3(1)
    func4(1)
    print("Completed after: {}".format(time.time() - start))

main()
```

The response that we got after executing this was:

```python
started func 1: 2
started func 2: 3
started func 3: 4
started func 4: 5
Completed after: 4.168870687484741
```

This saved us `~3` seconds for executing 4 functions. Now if we wanted to run 10000 such functions, we would save ourselves `~2000` seconds/ i.e. `35-40` minutes.

That's awesome, right.

These small savings can be very important to provide better user experience to your customers.

Now that we have understood the advantage of using `async` functions, we must know a few more things about it.

## Order of execution for async functions

We should understand that while running the functions in async mode, we don't really know about the order in which functions are executed. Let's understand the concept with an example.

The functions will return as soon as the execution is completed.

We can mock the different execution time by sleeping for a random time between 0 and 1 using, `random.randint(0, 10) * 0.1`.

Here is the full code.

```python
import asyncio
import time
import random
start = time.time()


def random_sleep_time():
    return random.randint(0, 10) * 0.1


async def async_sleep():
    await asyncio.sleep(random_sleep_time())


async def func1(a):
    await async_sleep()
    print("completed func {}: {}".format(a, a + 1))
    return a + 1


async def main():
    tasks = [func1(a) for a in range(0, 5)]
    await asyncio.gather(*tasks)
    print("Completed after: {}".format(time.time() - start))

asyncio.run(main())
``` 

The response to the following code is,

```python
completed func 0: 1
completed func 3: 4
completed func 1: 2
completed func 2: 3
completed func 4: 5
Completed after: 0.9764895439147949
```

## Practical Usage

After the release of Python 3.8, which moved the `asyncio.run()` method to stable API, you can start using it without any problem.

The only issue with moving from a `synchronous` approach to an async one is to change the way of thinking about the problem. You have to change the way you think about solving every problem. Once you reach that point, believe me, you will love it.

## How does it work?

Let's check the type of the async function.

```python
type(main())

# <class 'coroutine'>
```

So, the async function is of type `coroutine`.

This [GeeksForGeeks article](https://www.geeksforgeeks.org/coroutine-in-python/) does a very good job of explaining coroutines and subroutines.

To sum up what they wrote in the post, **subroutines** are the set of instructions that have one entry point and are executed serially.

On the other hand, **Coroutines** can suspend or give away the control to other Coroutines, allowing multiple tasks to run at the same time.

Python uses this concept to allow async behavior.

## Handling timeout

It is awesome to have a timeout for waiting for the task to get completed. We are not supposed to wait forever for it to complete. `asyncio` also provided the ability to add a timeout to the async function so that you can skip the execution before its completion.

A practical application of this can be a case when you are calling a third party API in your application and the third party itself is down. In that case, you don't want to wait for a long time.

You can use the `timeout` method to solve your problem. See the code for example:

```python
async def async_sleep():
    await asyncio.sleep(2)
    print('Execution completed')

async def main():
    try:
        await asyncio.wait_for(async_sleep(), timeout=1.0)
    except asyncio.TimeoutError:
        print('Timeout error')

asyncio.run(main())
```

The async function will raise `TimeoutError` if the coroutine doesn't return before the given `timeout` is passed.

Response after executing the above code is

```python
Timeout error
```

There are other awesome methods in the `asyncio` module.

You can check them at the [python website](https://docs.python.org/3/library/asyncio-task.html).

## Conclusion

If you want to provide a better and faster experience to your users, you can start using the `asyncio` for your application. This will definitely help you find cases in which you can reduce the execution time of your class.

Just forcing yourself to write in this way for few months can yield big returns in the future. 