---
author: Ranvir Singh
comments: true
date: 2017-09-10 23:08:37+00:00
layout: post
slug: permutations_smallest
title: Generating Lexographically smallest permutations
categories:
- Algorithm
- C/C++
---

Hello friends,

Today I was working on the latest online competitive question on CodeChef where I was able to find a good question. I was able to get the results for small input. The question was related to permutations. I was not aware on how can I write a working code that can find all the permutation of given set of numbers. So, I searched it online and found a good solution on geeks for geeks.

Here is the link to the problem.
- [CodeChef Problem statement](https://www.codechef.com/SEPT17/problems/MINPERM)

Here is the link to the solution for generating permutation having small complexity.
- [geeks for geeks](http://www.geeksforgeeks.org/heaps-algorithm-for-generating-permutations/)

I used the same approach to solve the problem. Most of the stuff is shared and is readable inside the code in the form of comments.

{% highlight cpp linenos %}
#include<bits/stdc++.h>

using namespace std;

/*
Algorithm to find permutations in own words

- Get the size of array, the whole array and number of elements
- i=0
- loop till i<n
- call itself with size=size-1
   - if the new size is odd
     - swap first and last element
   - if the new size is even
     - swap ith and last element

*/
// function to check if the update to smallest has made or not
void updateSmallest(int a[], int n, int smallest[]) {
    for(int i=0; i<n; i++) {
        if(smallest[i]>a[i]) {
            for(int j=0; j<n; j++) {
                smallest[j] = a[j];
            }
            return;
        }
        else if(smallest[i] == a[i]){
            continue;
        }
        else{
            break;
        }
    }
}

// function to check if the permutation is good or not
void checkGoodPermutation(int a[], int n, int smallest[]) {
    for(int i=0; i<n; i++) {
        if(a[i] != i+1) {
            if(i == n-1) {
                updateSmallest(a, n, smallest);
            }
        }
        else{
            return;
        }
    }
}

// function to print an array.
void printArray(int a[], int n) {
    for(int i=0; i<n; i++) {
        cout<<a[i]<<" ";
    }
    cout<<endl;
}

void permute(int a[], int size, int n, int smallest[]) {
    if (size==1) {
        checkGoodPermutation(a, n, smallest);
        return;
    }
    for(int i=0; i<size; i++) {
        permute(a, size-1, n, smallest);

        if(size%2==1) {
            swap(a[0], a[size-1]);
        }
        else {
            swap(a[i], a[size-1]);
        }

    }
}

int main()
{
    int t;
    cin>>t;
    for(int k=0; k<t; k++){
        int n;
        cin>>n;
        int a[n];
        int smallest[n];
        for(int i=0; i<n; i++) {
            a[i] = i + 1;
            smallest[i] = n;
        }
        permute(a, n, n, smallest);
        printArray(smallest, n);
    }
    return 0;
}
{% endhighlight %}

This is the working code for the small numbers. I am getting `time limit exceeding` for the large set. I have to make some optimizations to make it work for large numbers.

If you get some idea on how to optimize the code please share it with me using the comment section below. According to me current complexity of the code is: ```O(n*n! + n + n)```.

Thank you guys for reading.
