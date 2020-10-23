---
layout: post
title: Minimum Numbers of Function Calls to Make Target Array With Python
date: 2020-10-23T19:26:30.167Z
updated_date: 2020-10-23T19:26:30.193Z
description: Minimum Numbers of Function Calls to Make Target Array With Python
  Leetcode question with explanation on pythonprogramming.org
published: true
image: https://i.ibb.co/48LcZ1Z/carbon-3-2.png
tags:
  - python
  - competitiveprogramming
categories:
  - python
  - competitiveprogramming
author_name: EzzEddin Abdullah
author_username: ezz
show_ads: false
show_telegram_signup: true
---
{% include lazyload.html image_src="https://i.ibb.co/48LcZ1Z/carbon-3-2.png" image_alt="Minimum Numbers of Function Calls to Make Target Array With Python" image_title="Minimum Numbers of Function Calls to Make Target Array With Python" %}

Minimum Numbers of Function Calls to Make Target Array is problem number 1558 on leetcode and I am going to solve it using Python today.

## Understanding the Problem

[Minimum Numbers of Function Calls to Make Target Array](https://leetcode.com/problems/minimum-numbers-of-function-calls-to-make-target-array/) is a medium problem at leetcode, I hope you have read the problem carefully and have tried solving it. This problem requires you to get the least number of operations that you can do in order to get to the desired array. The question now, how we can do such operations to count its numbers to reach the target array in the least possible way.

## Initial thoughts

Let us take this example, having `[2, 2]` as the target array and we want to know the minimum number of operations to reach that array.

So we start off with `[0, 0]` adding 1 to each element (2 operations now) reaching `[1, 1]` and then multiply the whole array by 2 (1 operation) reaching the target array we want `[2, 2]` so we have 3 operations to reach the desired array for this example as shown below:

{% include lazyload.html image_src="https://uploads-ssl.webflow.com/5f359c073455c743bc873ee4/5f909c229bb26b9bb634e788_min_num_func_calls_1.png" image_alt="Minimum Numbers of Function Calls to Make Target Array With Python" image_title="Minimum Numbers of Function Calls to Make Target Array With Python" %}


But it's hard to move from `[0, 0]` to reach `[2, 2]` because of the possibility of wrong guessing of the next array we want to reach. What we can better do, is to move backward from `[2, 2]` to `[0, 0]` as indicated below:

{% include lazyload.html image_src="https://uploads-ssl.webflow.com/5f359c073455c743bc873ee4/5f909ddd15cb0a10a04b26d4_min_num_func_calls_2.png" image_alt="Minimum Numbers of Function Calls to Make Target Array With Python" image_title="Minimum Numbers of Function Calls to Make Target Array With Python" %}

In this case, we can divide instead of multiplying and subtracting instead of adding as shown in orange and we'll end up with the same number of operations.

## Better path

So now we have two main operations to be done: division and subtraction. It seems that we use division when all elements in the array are divisible by 2 but what if there is an odd number, we subtract.

The integer division can save us from worrying about the existence of odd numbers because even and odd numbers will be divided and what's left is the count of operations for every odd number existing which can be done by calculating the remainder. The remainder of any number by 2 is either 1 or 0.

If 1, we indicate that the number is odd and then we know that this is one operation.

Here are some scripts of how that integer division and the remainder are calculated in Python and Javascript:

Python

```python
#!/usr/bin/env python3

#https://leetcode.com/problems/minimum-numbers-of-function-calls-to-make-target-array/

def minfuncalls(nums):
    n = 0
    lennums = len(nums)
    print('>>', n, nums)
    while any(map(lambda e: e!=0, nums)):
        for i in range(lennums):
            n += nums[i] % 2
            nums[i] //= 2
        n += 1
        print('>>', n, nums)
    return n-1 if n > 0 else 0

def test(a,n):
    print(minfuncalls(a) == n, n)

test([0], 0)
test([0,0], 0)
test([0,1], 1)
test([0,2], 2)
test([2,4], 4)
test([1,5], 5)
test([2,2], 3)
test([4,2,5], 6)
test([3,2,2,4], 7)
test([2,4,8,16], 8)
```

## Acknowledgment

The Python code is mutual work with my best friend [Nour](https://github.com/noureddin). He actually has a contribution at gist for explaining a more efficient solution found on leetcode, please see this fantastic gist:‍

<script src="https://gist.github.com/noureddin/d2981404efd76cf15ec944639afe92a4.js"></script>

## Motivated by

*   [Array.prototype.some()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some)‍
*   [Minimum Numbers of Function Calls to Make Target Array](https://www.youtube.com/watch?v=4z6sgk9NELo&ab_channel=CompetitiveCoding)‍
*   [map(), filter(), and reduce() in Python with Examples](https://stackabuse.com/map-filter-and-reduce-in-python-with-examples/)
*   [Map, Filter and Reduce](https://book.pythontips.com/en/latest/map_filter.html)‍
*   [Integer division with remainder in JavaScript?](https://stackoverflow.com/a/4228376/4604121)