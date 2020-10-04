---
title: Mongo Aggregates and How to explain Aggregate queries
date: 2019-10-02T12:03:00.000Z
updated_date: 2020-04-04T19:57:13.529Z
description: Mongo aggregate explain with match, project, lookup, group and
  finally analysing how your aggregate query performed in mongo winningplan
published: true
image: https://i.imgur.com/vlIEICJ.jpg
tags:
  - database
  - mongo
  - nosql
  - node
categories:
  - database
  - nosql
  - mongo
  - node
---
{% include lazyload.html image_src="https://i.imgur.com/vlIEICJ.jpg" image_alt="Mongo aggregates with explain" image_title="Mongo aggregates with explain" %}

Today we are going to talk about Mongo Aggregates. A framework that helps us to run complex queries in Mongo DB. One of the best things that happened to Mongo.

Let's start by pulling out a few differences between the normal( SQL) and Mongo(NoSQL) database.

## Difference between SQL and NoSQL database

Mongo belongs to one of those NoSQL databases which disrupted the internet a few years ago. Everyone in the industry was talking about them. Everyone wanted to move their stack to these flexible databases.

Everyone was talking about how the data needs to move to that direction and so on.

As the hype began to settle, people started realizing the movement of the stack will help only if they implement it correctly and for most of them, the shift wasn't even necessary.

`NoSQL` is a wide term and that is used by a variety of databases. Mongo is also one of them, others being `Cassandra`, `Apache Spark` and many more.

MongoDB is a document-based, distributed database. In production, people tend to run it with 3 replicas. 1 is the master and the other two being the slaves. This provides redundancy and [high availability](https://en.wikipedia.org/wiki/High_availability).

You can configure these to follow any guidelines but by default reads and writes are handled by the primary replica and the new data is moved on to the replica sets on each database write.

As the mongo doesn't have a well-defined schema, it's pretty hard to make queries from the data.

Mongoose is a library that can help you with this. It provides a lot of benefits, like creating hooks and indexes easily on the collections.

> BTW, SQL table equivalent in Mongo is known as a `collection` and the row equivalent is known as a `document`.

Read more about the differences at [GeeksforGeeks](https://www.geeksforgeeks.org/difference-between-sql-and-nosql/).

## Mongo Aggregates

{% include lazyload.html image_src="https://webassets.mongodb.com/_com_assets/cms/mongodb_logo1-76twgcu2dm.png" image_alt="Mongo DB" image_title="Mongo DB" %}

Mongo DB aggregates make it easier to query data from different collections. It involves things like matching, getting data from other collections, selecting fields and many more.

> An aggregate is basically a set of operations where the result of one operation is passed on as an input to the next operation where each operation is applying some logic to get further insight from the passed data.

Let's discuss a few of these aggregate queries.

### Starting out a Mongo Aggregate

You can start the aggregate using the following code.

```javascript
db.collection.aggregate([aggregate pipeline commands], options)
```

where the collection is the name of the collection on which aggregate is applied and `db` is the instance of the connected DB object.

Following are the commands that you can use in the aggregate pipeline.

## Match in Mongo Aggregate

The match query can be called as the where query in SQL terms. You tell the aggregate to get the data that follows the given condition. It is recommended to keep the match query as soon as possible in the pipeline.

This will reduce the number of documents being returned from the query. It is also a good option to index the fields on which you run the match query to return the results faster.

For example: In a student database you can make this query as follows

```json
{ $match: { "roll_number": 901 }}
```

or

```json
{ $match: { "class": 5 }}
```

This query will return all the documents which satisfy the given query.

For all further parts of the pipeline, you can keep adding it to the main array of the pipeline.

**Note:** You can make use of the fields by appending a `$` to the name of the fields, whenever you want to use them.

### Use match as early as possible

You should use `$match` as early as possible to make use of `indexes`.

> `$match` operations use suitable indexes to scan only the matching documents in a collection. When possible, place $match operators at the beginning of the pipeline.

Always try to explain the `$match` part of your queries and prefer to create compound indexes according to your queries.

## Project in Mongo Aggregate

Project is the part where you tell the query which keys to pick from the given document.

```
{
    $project: {
        student_name: 1,
        student_age: '$age'
    }
}
```

This will pick up only the fields with value `1` in the document. It is important to reduce of data being transferred to next part of the pipeline.

It can also be used to change the name of the field. This is the `SELECT` equivalent of `SQL` commands.

`_id` field is added by default in the result. You can use `_id: 0`, if you don't want to include that field.

## Grouping in Mongo Aggregate

Group is used to group different things together, for example, if you want to calculate the sum of the age of students in different standards, the query will look something like this.

```
db.students.aggregate([
    { $group: { _id: "$class", total: { $sum: "$age" } } }
])
```

[Here is the link to the mongo query.](https://mongoplayground.net/p/-1e-TS53Tzf) You can use all different types of aggregate queries like average, min and max.

## Lookup other collections in Mongo Aggregate

Lookup is one of the most important aggregate queries which you can use. This allows us to join different collections together and get data from the other collections as well.

The simplest implementation of `$lookup` is as follows.

```
{
    $lookup: {
        from: <collection to join>,
        localField: <field from the input documents>,
        foreignField: <field from the documents of the "from" collection>,
        as: <output array field>
    }
}
```

[Here is the query of the lookup.](https://mongoplayground.net/p/rY_VqBk_XXE)

The lookup can be used with the pipeline as well. With this type of lookup, you can apply a check and tell the pipeline, when the given lookup will run.

```
{
      $lookup:
         {
           from: "students",
           let: { studentId: "$_id", age: "$age" },
           pipeline: [
              { $match:
                 { $expr:
                     { $eq: [ "$student_id",  "$$studentId" ] }
                 }
              },
              { $project: { student_id: 1, age: 1 } }
           ],
           as: "data"
         }
    }
```

This is the implementation that you want to use, when you want to run `$match` on the data being picked from the other collection.

## Unwind in Mongo Aggregate

Unwinding is a type of operation in which deconstructs an array field from the input documents to output a document for `each` element.

For example, consider this document: 

```json
[
  {
    "collection": "collection",
    "count": 10,
    "content": [
      {
        "k": {
          "type": "int",
          "minInt": 0,
          "maxInt": 10
        },
        "a": {
          "type": "int",
          "minInt": 0,
          "maxInt": 10
        },
        "b": {
          "type": "int",
          "minInt": 0,
          "maxInt": 10
        },
        
      },
      {}
    ]
  }
]
```

On applying `$unwind`,

```javascript
db.collection.aggregate([
  {
    "$unwind": {
      "path": "$content",
      "preserveNullAndEmptyArrays": true
    }
  },
  {
    "$project": {
      "_id": 0,
      "content": 1
    }
  }
])
```

We will get the following result,

```json
[
  {
    "content": {
      "a": {
        "maxInt": 10,
        "minInt": 0,
        "type": "int"
      },
      "b": {
        "maxInt": 10,
        "minInt": 0,
        "type": "int"
      },
      "k": {
        "maxInt": 10,
        "minInt": 0,
        "type": "int"
      }
    }
  },
  {
    "content": {}
  }
]
```

Check this on [Mongo playground](https://mongoplayground.net/p/iQsvZ3ZJ7AT).

## How to Explain mongo aggregate queries

To explain the queries, you will have to use the options in the aggregate to find the way in which queries are run.

```javascript
db.getCollection("author").explain().aggregate([
	{
		$match: {
		    "email" : "hello@heaven.god"
		}
	}
])
```

This will generate a simple output like this.

```json
{
    "stages" : [
        {
            "$cursor" : {
                "query" : {
                    "email" : "hello@heaven.god"
                },
                "queryPlanner" : {
                    "plannerVersion" : 1.0,
                    "namespace" : "db_name.author",
                    "indexFilterSet" : false,
                    "parsedQuery" : {
                        "email" : {
                            "$eq" : "hello@heaven.god"
                        }
                    },
                    "winningPlan" : {
                        "stage" : "COLLSCAN",
                        "filter" : {
                            "email" : {
                                "$eq" : "hello@heaven.god"
                            }
                        },
                        "direction" : "forward"
                    },
                    "rejectedPlans" : [

                    ]
                }
            }
        }
    ],
    "ok" : 1.0
}
```

`winningplan` contains an object which tells us more about the winning plan which was used to run the query and `queryPlanner` contains an `Array` of plans which were tried. Mongo chooses the best plans and uses it for running the queries.

If you use the `explain` with `executionStats` it will give you things like `docs Returned` and `docs Examined` which can be helpful in finding the best suitable `index` for your `collection`.

```javascript
db.getCollection("author").explain("executionStats").aggregate([
	{
		$match: {
		    "email" : "hello@heaven.god"
		}
	}
])
```

{% include lazyload.html image_src="https://i.imgur.com/gls7IHT.jpg" image_alt="Explain mongo aggregate queries" image_title="Explain mongo aggregate queries" %}

## Conclusion

There are a few more options to choose from. Aggregate is one of the most important parts of the Mongo Database.

If you are dealing with this Database daily, then it would be useful to know a little about it as well.

Thanks for stopping by, Let me know if you want to know about something else as well. I love to write about tech topics.

Also, let me know if I have made any mistake in this post.

**Note:** The internal [performance optimizer](https://docs.mongodb.com/manual/core/aggregation-pipeline-optimization/) of the mongo aggregate optimizes the queries accordingly to make them as fast as possible.
