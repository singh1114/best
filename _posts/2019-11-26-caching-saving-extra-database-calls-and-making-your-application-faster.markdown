---
title: 'Caching: Saving extra database calls and making your application faster'
date: 2019-11-26 21:16:00 Z
published: false
---

Caching is a way of stopping the server from hitting some time taking resources and sending the data before hitting that time taking resources. In most of the cases, these time taking resources are databases. This helps to improve the user experience by delivering stuff faster to the users.

Caching is not straight forward. You will have to design your caching strategies in a way such that users are not served some old data and at the same time your servers are not facing some unnecessary load.

> More the time taken by a given request more is load on your servers.

## For whom this post is not for

This post is not for individuals who are working on getting their product right. You have to work on things like getting it right, rather than getting it fast.

Also, this post is not for the people whose products provide different data to all the individuals all the time. You will have to make that extra call to bring out the new data anyway.

In this post, we will be discussing the following things.

## How caching is helpful

Caching is helpful 

## At what levels we can cache data

## Nginx( Server) level caching

## Cloudfront level caching for frontend apps

## Caching using Memcache

## Caching using Redis