---
title: Mongo Aggregates
date: 2019-10-02 12:03:00 Z
published: false
categories:
- mongo
- nosql
- database
- aggregates
tags:
- database
- mongo
- nosql
---

Today we are going to talk about Mongo Aggregates. One of the best things that happened to Mongo.

Let's start by pulling out a few differences between the normal and Mongo database.

Mongo belongs to one of those NoSQL databases which disrupted the internet a few years ago. Everyone in the industry was talking about them. Everyone wanted to move there stack to these flexible databases.

Everyone was talking about how the data needs to move to that direction and so on.

As the hype began to settle, people started realizing the movement of the stack will help only if they implement it correctly and for most of them shift wasn't even necessary.

`NoSQL` is a wide term and consists of a variety of database models. Mongo is also one of them, others being `Cassandra`, `Apache Spark` and many more.

MongoDB is the document-based, distributed database. In production, people tend to run it with 3 replicas. 1 is the master and the other two being the slaves. This provides redundancy and high data availability.

You can configure these to follow any guidelines but by default reads and writes are handled by the primary replica and the new data is moved on to the replica sets on each writes.

As the mongo doesn't have a well-defined schema, it's pretty hard to make queries from the data.

Mongoose is a library that can help you with this. It provides a lot of benefits, like creating hooks and indexes easily on the collections.

BTW, SQL tables in Mongo are known as `collections` and rows are known as `documents`.

**Aggregates**

Mongo DB aggregates make it easier to query data from any collection. It involves things like matching, getting data from other collection, selecting fields and many more.

Let's discuss a few of these aggregate queries.

**Match**

The match query can be called as the where query. You tell the aggregate to get the data that follows the given condition.
