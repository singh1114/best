---
title: Building RESTful APIs with Java Spring Boot framework | For Beginners
date: 2019-10-28 21:14:00 Z
categories:
- API
- Spring Boot
- Technology
- java
tags:
- Programming
- Technology
- java
---

Java is one of the most widely used programming languages in the world. Not only it is widely used, but it is also being used as the core part of the top software companies in the world. So, if your dream is to work for those top companies, you better know a little bit of Java.

This tutorial will help you to create a CRUD(Create, Retrieve, Update and Delete) based application. In this tutorial, we will create every API for a **school management system.**

## Outcome and Goals

After going through this guide, you will be able to build complex applications using Spring Boot framework.

I would encourage you guys to create a small project of your own as well, as we move forward in this guide.

## Why Spring Boot?

While building a web application, the main goal of the developer is to get the application out as quickly as possible. The developer should not be worried about the configuring various layers of the system.

Spring Boot helps us to remove that hassle and helps us to build us stand-alone, production-ready applications that **Just works**.

With that definition, you might be feeling that this framework is just for small level applications. But that is not true. You can build fairly complex systems using this framework.

## Why not use Spring directly?

There are a lot of reasons why people started moving on from the Spring framework to the smaller level frameworks. One of them which makes the most sense is the complexity.

As Spring itself is a huge framework, its not always easy to get started and build the application.

You need to know a lot of things before you can start building the application.

Spring framework was originated to solve the commonly occurring problems in the Companies and providing a single framework that can solve them all. But as time went by, building a simple CRUD based application become pretty hard in the case of Spring framework and Spring Boot came to the rescue.

### What do we need?

**1. Text Editor (IntelliJ Idea: Community Version)**

Most of the Java developers make use of the official IDE provided by the IntelliJ community for carrying out the development work of there project. We are going to use this as well.

**2. Maven**

Maven is used for handling the packages required to run the application and other basic requirements to make it work. This helps us to handle all the dependencies easily.

Without Maven, you will have to download each and every dependency and download all the jar files and handle the full cycle of updates which itself is a quite hectic process.

Maven does it by introducing an XML file that contains the name and version of the package that you need for the development of the given project. This file is known as `pom.xml`.

**3. Java 8 or Above**

I will be working on Java 8 in this tutorial. You will also have to JAVA_HOME environment variable as well.

Try running these two commands to find if you are set up properly or not.

```bash
java -version
```

It should give you output like as follows:

```bash
java version "1.8.0_221"
Java(TM) SE Runtime Environment (build 1.8.0_221-b11)
Java HotSpot(TM) 64-Bit Server VM (build 25.221-b11, mixed mode)
```

For setting `JAVA_HOME`, try this:

```bash
echo $JAVA_HOME
```

Result for MAC will be,

```bash
/Library/Java/JavaVirtualMachines/jdk1.8.0_221.jdk/Contents/Home
```

## Let's start

Open up your IDE and create a Maven project with basic defaults selected. Choose some random GroupId and Artifact ID.

![java_new_project](https://i.imgur.com/GchFM89.jpg "Java New project"){:class="lazyload"}

![java_choose_project](https://i.imgur.com/If10F0g.jpg "Java New project"){:class="lazyload"}

![java_choose_group](https://i.imgur.com/LRzxxES.jpg "Java New project"){:class="lazyload"}

![java_finish](https://i.imgur.com/NEWTCbN.jpg "Java New project Finish setup"){:class="lazyload"}

## Setting up pom.xml

Find the `pom.xml` file and add the following configuration.

<script src="https://gist.github.com/singh1114/ff9bd0764f03168b4b6276d1f5079459.js"></script>

The `parent` part in the file tells that we are going to use given parent and include all the jars that are present in the given group and given version.

After adding this data to your `pom.xml` file you will have to update the Maven. In most of the cases, you will see a notification in the IDE itself to update it. Otherwise, you can find it in the IDE's navbar.

## Setting up the entry point of the spring boot project.

Now that our dependencies are sorted, let's start by building the entry point to the project.

To set up the entry point, create a package in the directory `src/main/java` with whatever name. In the package create a Java class with a name of your choice.

<script src="https://gist.github.com/singh1114/960d3f4147cfee37d6d5599fbf50c489.js"></script>

First line contains the name of the package that you created. In the 6th line, you are letting the Spring Boot framework know that this entry point of the project by annotating the class which contains the main class.

For starting the server you have to call a server starting function with the following line.

`SpringApplication.run(RestAPI.class, args);`

This is all that was required to build the initial server in Spring Boot.

You can click on the `Run` button. This will run the application. You will see the following output.

![compilation_response](https://i.imgur.com/dxAohR4.png "spring boot compilation response"){:class="lazyload"}

Now that the server is started, you can head out to the browser and type in `http://localhost:8080` to find the server.

You will get the following error message.

![browser](https://i.imgur.com/tj7u8lU.png "localhost response"){:class="lazyload"}

That was really easy. It's really easy to setup a server using the Spring Boot framework. Now we will work to create Controllers and various other things to create a proper set of Rest APIs.

## Let's add a controller

Now that we have a simple server set up, let's move forward and create a valid URL that we can hit and get the response back. For the testing purpose, I am going to create the status API. This API will tell us whether the services of the server are up or not.

For this purpose, you will need to have a class annotated with `RestController`. For more information, you can learn more about the MVC framework.

Spring Boot allows us to simply create controllers where we can specify which URL is going to be used to run this particular code.

<script src="https://gist.github.com/singh1114/0aa7c518315f1009f5c7825e65f30e1a.js"></script>

Create a file called `StatusController.java` in `io.singh1114.springboottut.status` package and add the following code.

`RestController` is the part of the code that tells the Spring Boot that this class should be treated as a controller.

Once we have this, we can use the methods which can be used by any controller and written in RestController static class.

`RequestMapping` takes two arguments, where you have to specify path and API Method( GET, POST, PUT). But if you don't specify anything, it takes GET by default.

Rerun the application and head to `http://localhost:8080/status/`.

You will get the **We are up!** message.

## Return Data from the Controller

Now, let's try to pass back data from the Controller.

We are going to start with a basic `StandardController.java` and `Standard.java` class in the `io.singh1114.springboottut.standard` package.

<script src="https://gist.github.com/singh1114/30a01779d59b1f40e03a9da5e8dbf777.js"></script>

In the `Standard.java` file, we are defining the schema of the standard class along with the `getter`, `setter` and `constructor` functions. These functions will help us to set and get the data for various class variables.

In the `StandardController.java` file, we are using the same method that we used last time to create an API that allows the `GET` method with `/standards` endpoint.

This time the function is returning back the List data to the endpoint. `Spring Boot` helps us convert the data in the List to valid `JSON` and sends back the data.

Here is how it is going to look on the browser.

![standards_api_response](https://i.imgur.com/S6O8NnB.png "standards api response"){:class="lazyload"}

## Let's think about data

As we have already know how to set up a basic Rest API, we now are going to think about the system that we are going to create in this guide.

For the sake of this tutorial, we are going to work with three entities `School`, `Standard` and `Students`.

**1. Each school can have multiple standards.**

**2. Each Standard can have multiple Students.**

Let's start with the `School` entity.

For all operations of a **School**, we will need the following methods.

1. `GET` - `/schools` - Get all schools.
2. `GET` - `/school/id` - Get info of the given school.
3. `POST` - `/school` - Create new School.
4. `PUT` - `/school/id` - Update info of the school.
5. `DELETE` - `/school/id` - Delete the school.

## Let's add a persistence layer: Database

Now that we have agreed upon the basics of the APIs that we are going to develop, let's just add a persistent layer that can persist data. There is a name for adding this persistence layer to the Java, called [Java Persistence Layer( JPA)](https://docs.oracle.com/javaee/6/tutorial/doc/bnbpz.html).

JPA is a type of ORM( Operation Relational Manager). If you have worked on some other framework, you might have heard about this term. An ORM helps us to reduce our effort by providing build-in methods to query data from the database.

We are going to use `MySQL` for the tutorial purpose. You can go forward and choose any of the databases out there. The only thing that you will have to change is the libraries that you are importing, everything else should stay as it is.

## Setting up MySQL

* You can install MySQL using a simple `brew` command in MAC.

```bash
brew install mysql
```

For Linux, you can try this command.

```bash
sudo apt install mysql
```

* Then you can start the MySQL server using the command.

```bash
brew services start mysql
```

* Now you will have to create a database for the Spring Boot application to interact with.

```bash
mysql -u root --password
```

* Once, you are inside the MySQL shell, you can create the database using this command.

```bash
create database springguide;
```

* Once you are done with database creation, you can add this content to the file `src/main/resources/application.properties`.

```bash
spring.datasource.url=jdbc:mysql://localhost:3306/springguide
spring.datasource.username=root
spring.datasource.password=<Your password>
spring.jpa.hibernate.ddl-auto=update
```

**Note:** The first line tells the URL at which Spring could find the database connection.

Second-line gives the username of MySQL who is the owner of the database.

The third line is the password of the database.

The fourth line is the setting that will help you to auto-generate the tables in the database.

Just try to build the application once done with the setting. It should build without any error.

## Build the school Model.

Here is what `io.singh1114.springboottut.school/School.java` file looks like.

<script src="https://gist.github.com/singh1114/bf5ca2f2f1bfbbf5daeb78f09f56260f.js"></script>

After writing this down, run the application and check the MySQL shell to find the table created.

![mysql shell](https://i.imgur.com/NFGMhfq.png "MySQL shell"){:class="lazyload"}

`Entity` is the keyword that tells the Spring Boot that the following class should be considered as a table class. Class parameters are fields of the table.

```bash
    @Id
    @GeneratedValue(strategy = GenerationType.AUTO)
    @Column(name="id")
```

With these lines, we are letting the Spring Boot know that the field which is annotated with `Id` keyword, will be treated as `Primary key`. `GeneratedValue(strategy = GenerationType.AUTO)` tells Spring Boot to autogenerate the value of id field( By incrementing the field)and `Column` field specifies the column name. These are required only if we are doing something else than the normal stuff.

## Let's make the Db Access layer (Repository)

The database Access layer in Java is given the name of the Repository. A simple repository provides all the basic methods required to find, create and delete entries in the database.

Add this code to `io.singh1114.springtut.school/SchoolRepository.java`

```bash
package io.singh1114.springboottut.school;

import org.springframework.data.repository.CrudRepository;

public interface SchoolRepository extends CrudRepository<School, Long> {
}
```

Basically you have to extend the `CrudRepository` and create an interface of that. In the params, you have to pass the name of the Java class that you want to extend and type of the primary key being passed (`<School, Long>`).

We can create another file to handle interactions with the DataBase by creating a Service layer. In Java, it is generally done to separate the business logic from `Controllers`.

The advantage of using such a service is that Java while building will load all the classes marked as business services as a `Singleton` and it will not have to create an object again and again.

We can do that by using the `@Service` annotation. Here is the content of `io.singh1114.springboottut.School/SchoolService.java` and corresponding `Controller` code.

<script src="https://gist.github.com/singh1114/5f21641afd022ce975f9ba38e5601f1d.js"></script>

Looks like we have already discussed most of the stuff in here. Please drop your comments if you are stuck somewhere.

Now you are ready to run your application with DataBase connected.

![Empty Schools response Postman](https://i.imgur.com/E4e1h4F.png "Empty Schools response Postman"){:class="lazyload"}

![Add School Postman](https://i.imgur.com/BGbQfq0.png "Add School Postman"){:class="lazyload"}

![Schools response Postman](https://i.imgur.com/dBUVcgY.png "Schools response Postman"){:class="lazyload"}

That's all for this part of the guide. With this much knowledge of Spring Boot, you can create any level of complex project( With a bit of googling).

Your reviews are very important. Please leave your reviews in comments section below.

You are awesome.