---
layout: post
title: Substring Removal Game with Python
date: 2020-10-23T20:22:48.036Z
updated_date: 2020-10-23T20:22:48.059Z
description: Substring Removal Game with Python - codeforces problem solution on
  pythonprogramming.org
published: true
image: https://i.ibb.co/n11fXtn/carbon-6-1.png
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
{% include lazyload.html image_src="https://i.ibb.co/n11fXtn/carbon-6-1.png" image_alt="Substring Removal Game with Python" image_title="Substring Removal Game with Python" %}

## Understanding the Problem

[Substring Removal Game](https://codeforces.com/contest/1398/problem/B) is an 800-point problem at codeforces, I hope you have read the problem carefully and have tried thinking about solving it. This problem basically states as its name sounds to say, to remove a substring.

Per each test, you're given a string of binary characters (0's and 1's) and you're required to remove each consecutive 1's to make Alice win. Who is Alice? Alice and Bob are players in the game, and the winner is the one who removes the highest numbers of 1's. Your duty is to make Alice win given that Alice is the first to move.

## How to Think for a Solution

This problem has two inputs:

*   input for test cases
*   input for each string of binary characters per each test case

You can think of this problem as capturing all consecutive ones in the string first and then we can make a decision on which 1's we should focus on to make Alice win. 

For example, if the input is 01111001 this means that we have 4 consecutive 1's and then just 1; to make Alice win in this case, we should make her take that move which is obviously her first move already and then Bob can take the second move which is the last 1 in the string.

Let's have another example, 111111 these are 6 ones which can be the first move for Alice so 6 moves will be her win.

How about this tricky one: 101010101?

So there are 5 ones... which of them should be Alice's moves? That would be the first and the third and the fifth... so here 3 moves for Alice.

What for this one: 011011110111?

Here, we have 2 consecutive ones, 4 consecutive ones, and 3 consecutive ones. Which moves can make Alice win?

So we need then to think how we can make number of moves the highest possible so if we sort numbers of consecutive ones in descending order and then start on the highest number that would give us the first move for Alice, and the second move should be a step two from that one. So in this case: `[4 3 2]` Alice will take moves 4 and 2 which sum up to 6.

That's how I thought about this problem and below is my implementations in Python:

## Python Solution

‍```python
N = int(input())
s = []
for _ in range(N):
    s.append(input())

for n in range(N):
    ones = []
    count = 0
    for c in s[n]:
        if c == '1':
            count += 1
        else:
            if count:
                ones.append(count)
                count = 0
    if count:
        ones.append(count)

    onessorted = sorted(ones, reverse=True)
    print(sum(onessorted[0::2]))
```

## Shoutout

I'd like to share [this video](https://www.youtube.com/watch?v=xE8qf5sfn4Y&ab_channel=codeExplainer) because the idea of solving this solution is from this guy. Check out his solution in C++ if you're interested.