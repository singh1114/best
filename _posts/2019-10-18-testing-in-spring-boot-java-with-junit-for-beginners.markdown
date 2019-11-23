---
title: Integrity testing of APIs in Spring-Boot( Java) with Junit | For Beginners
date: 2019-10-18 22:48:00 Z
published: false
categories:
- java
- springboot
- testing
tags:
- java
- springboot
- testing
---

Shipping your product without testing is like selling a car without turning on the engine. You have to run a few tests again and again while the development of the product and if those tests are not automated, you will have a hard time to test your application.

![Spring boot logo](https://imgur.com/BEIqT5f "Spring boot logo")

This post is in continuation of the last post we shared related to Spring boot in which we shared on how to write [Rest APIs in Spring Boot.](https://singh1114.github.io/blog/building-restful-apis-with-java-spring-boot-framework-for-beginners/). Please go through that post if you want to learn on how to create rest APIs using Spring Boot.

In this post, we are going to discuss the way in which you can test your spring boot application from start to end without any mocking.

First of all, we have to add the `test` libraries to the `pom.xml`, so that maven can install them for us.

Here is the code to add testing libraries to `pom.xml`

```xml
        ...
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
        </dependency>
```

Now since we are going to test the application from end to end, let's create a controller test.

...