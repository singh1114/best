---
title: Building RESTful APIs with Java Spring Boot framework | For Beginners
date: 2019-10-11 21:14:00 Z
categories:
- java
- API
- Spring Boot
tags:
- java
- programming
- tech
---

Java is one of the most widely used programming languages in the world. Not only it is widely used, but it is also being used as the core part of the top software companies in the world. So, if your dream is to work for those top companies, you better know a little bit of Java.

This tutorial will help you to create a CRUD(Create, Retrieve, Update and Delete) based application. In this tutorial, we will create every API for a **school management system.**

## Outcome and Goals

After going through this guide, you will be able to build complex applications using Spring Boot framework.

I would encourage you guys to create a small project of your own as well as we move forward in this guide.

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

![java_new_project](https://i.imgur.com/GchFM89.jpg "Java New project")

![java_choose_project](https://i.imgur.com/If10F0g.jpg "Java New project")

![java_choose_group](https://i.imgur.com/LRzxxES.jpg "Java New project")

![java_finish](https://i.imgur.com/NEWTCbN.jpg "Java New project Finish setup")

## Setting up pom.xml

Find the `pom.xml` file and add the following configuration.

<script src="https://gist.github.com/singh1114/ff9bd0764f03168b4b6276d1f5079459.js"></script>

The `parent` part in the file tells that we are going to use given parent and include all the jars that are present in the given group and given version.

After adding this data to your `pom.xml` file you will have to update the Maven. In most of the cases, you will see a notification in the IDE itself to update it. Otherwise, you can find it in the top bar.