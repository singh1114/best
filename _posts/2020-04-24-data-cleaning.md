---
layout: post
title: Data Cleaning
date: 2020-04-24T18:35:38.721Z
updated_date: 2020-04-24T18:35:38.738Z
published: false
show_ads: false
---
Data collection and cleaning is one of most important part of the Machine Learning process. Surveys show that Data cleaning and manipulation is the part where most of the data scientist spend nearly the 60% of their time during the development of a machine learning model.

Data include a lot of errors, Missing values, typos, mixed formats and duplicity are a few of them. Data cleaning consists mainly two parts

* Error Detection, in which our main aim in to detect different types of errors in the data.
* Error Repair, in which our main aim is to clean the data by using different algorithms. We will discuss most of them in this post.

These steps when done practically are generally outlined as follows:

## Outlier Detection

The definition of an outlier can depend on the application of the problem.

Generally,

> Outlier is an observation or dataset which deviates a lot from the other observation such that it raise suspicion that the dataset was created by some false engine.

We need to define outliers specifically for your problem. One example of data outlier can be the salary data of a company where the salaries of a given department are around `$100,000`, and an employee getting `$10,000`.

## Data Deduplication

The whole process of removal of duplicates in the data is known as data deduplication process.

Duplicate detection is the process of detecting duplicates in the data. There are a lot of ways in which you can end up with duplicate data in your dataset. For example a customer using different names while shopping on your website.

Considering this and a lot of such customers different can lead a fairly different model but if we can spend some time in detecting the similarity between these special customers by using some similarity, we can improve our model to great extent.

This step might include designing similarity metrics for your data 