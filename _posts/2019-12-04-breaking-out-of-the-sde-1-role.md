---
title: Breaking out of Software Developer-I role as a web developer
date: 2019-12-04 20:01:00 Z
categories:
- discuss
- programming
- webdev
- career
tags:
- discuss
- programming
- webdev
- career
image: https://i.imgur.com/aV8yfFk.jpg
---

This article is not for the people who are still looking for a first job as a developer. This is for the people who are in their first job and want to learn things so that they can make that big shift in their career. There must be a guide that can tell, how much work is left.

![Breaking out of software development - I role](https://i.imgur.com/aV8yfFk.jpg "Breaking out of software development - I role")

**Note:** In this post, I am only going to share the pathway for a backend engineer. I would be happy to add if someone comes up with a similar pathway for `frontend`, `DevOps` or a `data scientist` role.

I am sure that this transformation will take some time along with your daily work. As you keep on facing new challenges every day in your day job, you should be working to learn these skills.

## Learn Database designing

This is considered as one of the most important soft skills which you should have so that you spend lesser time making changes to the database design during the later stages of the development.

Changing database design will probably take the most time during a code review. You should spend a good amount of time thinking about the way you should keep your data.

This is also applicable to the people who use the NoSQL database. It's always good to have at least some structure in the database which makes it easier to understand the logic of the code and will help you to debug it afterward.

Some of the important things that you should know are:

### Indexing

Indexing is a way of making your search faster while querying the data from the database. Almost all of the applications involve some interactions with the database.

You want to deliver the requests as quickly as possible so that your customers can have a better user experience. We will discuss indexing in much more details in the subsequent posts.

### Foreign keys

Foreign keys are used to define the relationship between two tables. For example, a school can have multiple classes. So, we make two separate tables `School` and `Class` with the `School` table having a foreign key of `Class`.

The foreign key relations can be of multiple types, `One-to-one`, `one-to-many` or `many-to-many`. The foreign key creates a new column in the child table and saves an `address` of the corresponding row of the parent table.

While creating the foreign keys you can specify, what you want to do when the rows in the parent table are deleted.

In a framework like Django, you can choose from a [number of options.](https://docs.djangoproject.com/en/3.0/ref/models/fields/#django.db.models.ForeignKey.on_delete)

* `CASCADE`: Deletes the child rows as well.
* `SET_NULL`: Set the value to null.
* `PROTECT`: Stops you from deleting the parent row.
* `SET_DEFAULT`: Set to a default value of the column.
* `SET`: Set to the given value.

### Primary Keys

The primary key is the field which should be unique for every row in your table. For example, the roll number would be unique for a class table. Also, it should be part of many vital queries while fetching data from the database.

![Primary key in MySQL](https://i.imgur.com/GK763MW.jpg "Primary key in MySQL")

`id` is the primary key in the above picture.

### Joins

Joins are used to get the data from two SQL tables at the same time.

### Normalizing

> Normalizing is the concept of dividing the tables into smaller tables so that it reduces redundancy and dependency on other tables.

All these concepts are used to structure your tables better. Most of the databases create default Primary keys in their tables/ Collections. You should learn to create relations in a better way so that you don't have to change the schema in the future.

## Learn some DevOps

You don't really need to know much about the stuff but a basic understanding of things will always help. It's good to know about EC2s.

Also, sometimes you have to debug stuff related to DevOps, which might take you to see different logs all over the places.

Maybe database instances are down or Redis is not working properly or Maybe `queue` is chocked or `SNS` is not being fired or a given `lambda` is not being triggered.

There is a whole lot of stuff in the AWS console, you just need to know a few of the terms to get going in this case.

Always prefer to use shell rather than using editors for simple things to get you into the habit of using the shell.

## Learn how to debug

One of the most important things that working on a problem teaches you is that you learn how to debug properly. Learn how to run the debugger in the language of your choice.

Learning how to add breakpoints to your code can be advantages to you as well.

## Learn to write tests

{% include linked_post.html url="how-to-use-factoryboy-to-create-model-instances-in-python-for-testing" %}

I have written a lot of posts related to tests. It's always better to test your code using the tests rather than having a manual tester doing it for you. It's always slower than having a Continuous integration platform setup running tests every time you push new code to some branch.

## Learn about scaling issues

You do have to change your solutions according to the scale that you face in the production. If you are getting a few 100 users coming to your product daily, you can keep the screws loose.

On the other hand, if millions of users are visiting your product daily, you will have the change the way you are providing the solution.

You might have to add caching at different places so that you can give a faster response and reduce the overhead on your database saving you a ton of money. You will have to tweak your queries a little to reduce the size of the response.

Always keep [Donald Knuth](https://en.wikipedia.org/wiki/Donald_Knuth)'s words in your head before optimizing things,

> The real problem is that programmers have spent far too much time worrying about efficiency in the wrong places and at the wrong times; premature optimization is the root of all evil (or at least most of it) in programming.

## Learn a little bit about security

Learning a little bit about the security vulnerabilities can help to keep the attackers away from your application and your user data.

Keep a check on the ports that are open on the EC2 on which you are running your application. I have seen people keeping all the ports open on the EC2s on which they are running their production application.

Also, keep a check on your S3 buckets if you providing secure data using the S3 buckets to your customers.

## Learn about caching

Learning about various places where you can cache the response for faster delivery is very important. Caching the data using Cloud front or caching it using Redis.

You can do a whole lot of things with caching.

## Learn to review code properly

Reviewing the code is an art that you learn over time by reading and writing a lot of code written by a variety of people. Reviewing the code is also the fastest way of learning to write the code as well.

## Maintain your personal websites

Along with the personal blog, you can maintain and personal project website as well. Showing your projects to the world for reference. You can use something like [Heroku](https://www.heroku.com/) to publish your applications.

## Share your learnings

Share your learnings with the world. It's a good idea to create a personal blog. With GitHub pages and Jekyll, it's fairly easy to start your personal blog as a developer.

I have written a lot of posts related to [blogging with Jekyll](https://ranvir.xyz/blog/blogging/), do have a look at them.

## Help out new joiners and business guys

Growing personally is not just about learning new stuff, its also about helping others as well. You should help the new joining to settle down and make them aware of the tools that you use to make your life easier.

Every now and then, business guys ask you to look into the stuff they are stuck at. Help them out every now and then. They help you know your system in a better way.

Thanks for reading the post. Drop a like and share the post with your friends. Also, join the subscription if you want to read such posts every week.