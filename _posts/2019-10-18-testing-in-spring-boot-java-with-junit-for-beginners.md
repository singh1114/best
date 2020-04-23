---
title: Integration testing of APIs in Spring-Boot( Java) with Junit | For Beginners
date: 2019-10-18T22:48:00.000Z
updated_date: 2020-04-10T07:40:22.826Z
description: "Writing integration tests for your spring boot application using
  junit without mocking Db and using different test profile is one of the best
  things you can do for your future self. "
published: true
image: https://i.ibb.co/C27KWdk/Untitled-presentation-1.png
tags:
  - java
  - springboot
  - testing
categories:
  - java
  - springboot
  - testing
show_ads: false
redirect_from: []
---
{% include lazyload.html image_src="https://i.ibb.co/C27KWdk/Untitled-presentation-1.png" image_alt="Integration testing in spring boot | Java" image_title="Integration testing in spring boot | Java" %}

Shipping your product without testing is like buying a car without turning on the engine.

We have to run a few tests again and again during the development of the product and if those tests are not automated, we will have a hard time testing our application.

Here is a post that will help you to understand the importance of writing tests?

{% include linked_post.html url="how-to-write-testable-code-that-can-scale-with-examples" %}

This post is in continuation of the last post we shared related to Spring boot in which we talked about writing Rest APIs in Spring Boot.

{% include linked_post.html url="building-restful-apis-with-java-spring-boot-framework-for-beginners" %}

Please go through that post if you want to learn how to create rest APIs using Spring Boot.

In this post, we are going to discuss how we can test our spring boot application from start to end without any mocking.

{% include lazyload.html image_src="https://i.imgur.com/BEIqT5f.jpg" image_alt="Spring boot logo" image_title="Spring boot logo" %}

First, we have to add the `test` libraries to the `pom.xml`, so that the Maven can install them for us. Here is the [GitHub Repo](https://github.com/singh1114/java_tutorial) that contains the code for this tutorial.

Here is the code to add testing libraries to `pom.xml`

```xml
        ...
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
        </dependency>
        <dependency>
        ...
```

## Using separate config for testing purposes

We don't want to add the data to the same database as of the production one. So, we will start by creating a separate configuration for handling the test cases. Also, its always a good practice to have separate configurations anyway.

Create a new resource file, `src/main/resources/application-test.properties` and add the following data to it.

<script src="https://gist.github.com/singh1114/83a86ec1ad07822b4d03813981b47e86.js"></script>

**Note:** We will have to create the database in our local system to make it work.

Now that we have a separate configuration file, we have to export it as an App configuration so that we can use it in the tests itself.

Add the following code to the file, `src/main/java/io/singh1114/springboottut/AppConfigurationTest.java`

<script src="https://gist.github.com/singh1114/df676e3dae7ab7ccb48e64574dd94916.js"></script>

## Writing Controller test for Spring Boot API.

Now since we are going to test the application from end to end, let's create a controller test.

Add the following code to `src/test/java/io/singh1114/springboottut/SchoolControllerTest.java`

<script src="https://gist.github.com/singh1114/a305379be45ef7924d14d776756caa55.js"></script>

Let's go through the file and understand this.

`@ActiveProfiles`, is used to let the framework know that we are going to use the given profile. As we have already declared the `test` Profile in the `Configuration` file, we can use it here directly.

`@RunWith` and `@SpringBootTest` is used to start a simple server to carry out the tests using the `SpringBootFramework`.

## Running on a random port

With `SpringBootTest.WebEnvironment.RANDOM_PORT` we are telling the framework to launch the application on a Random PORT.

## Removing any change made to the database after test completion.

`@Transactional` will help us to clean the database once tests are completed. We don't want to keep adding stuff to the database and want to clean it after every test run.

Wrapping something with `Transaction` is a very general programming concept which is present in almost every Database. According to this, if you run any number of SQL commands inside the transaction and if it fails on any step, the whole transaction will be reverted.

This is fairly useful when you are running related commands, for example, reducing the inventory size and adding stuff to someone brought list.

The same concept is used here, the only hack is that anything you run inside `@Transactional` is rolled back in the end.

Read more about this on [Spring boot logs](https://docs.spring.io/spring/docs/4.2.5.RELEASE/spring-framework-reference/html/integration-testing.html#testcontext-tx).

## Creating the API endpoint

```java
    @LocalServerPort
    private int port;

    private String createURLWithPort(String uri) {
        return "http://localhost:" + port + uri;
    }
```

These are used to create the URL for a given endpoint to hit.

## Creating the School Object

```java
    @Autowired
    private SchoolRepository repository;
    ...
        School testSchool = new School(1, "First Location", "Mr. Ranvir", "California");
        repository.save(testSchool);
    ...
```

This code is used to create the object in the database.

## Sending the request and getting the response

```java
    TestRestTemplate restTemplate = new TestRestTemplate();

    HttpHeaders headers = new HttpHeaders();
    ...
        HttpEntity<String> entity = new HttpEntity<String>(null, headers);

        ResponseEntity<String> response = restTemplate.exchange(
                createURLWithPort("/schools"),
                HttpMethod.GET, entity, String.class);
    ...
```

## Checking if the response is equal to the object created

```java
JSONAssert.assertEquals(expected, response.getBody(), false);
```

Here we are checking if the body of the response is equal to the expected response.

## Run the tests

Use can use the following command to run the tests.

```shell
mvn test
```

{% include lazyload.html image_src="https://i.imgur.com/dyU6gXj.png" image_alt="Spring boot test passing" image_title="Spring boot test passing" %}

## Creating Maven Spring Boot CI pipeline using CircleCI

It is very important to automate the process of running the tests before merging the code to the master branch and deploying it. [CircleCI](https://circleci.com/) is a good service which can help you to create [CI](https://en.wikipedia.org/wiki/Continuous_integration) pipelines for your project.

CircleCI will try to run the project according to the configuration specified in a special `yml` file.

### Login to CircleCI and turn on the test for the repository

You can easily log in to Circle CI using your GitHub or Bitbucket account. After that you can turn on the CI pipeline by clicking on `Set up Project` button for that repository.

{% include lazyload.html image_src="https://i.ibb.co/1MJd984/Screenshot-2020-04-24-at-12-52-04-AM.png" image_alt="Circle Setup Project" image_title="Circle Setup Project" %}

In the next step it will ask you about the language of the project. You can choose any and according to your choice it will create a branch with `.circleci/config.yml` file in the root directory.

After a lot of tweaks to the config file that CircleCI created for me, I ended up with this.

```yml
version: 2.1
  
jobs:
  build:
    docker:
      - image: circleci/openjdk:8-jdk
      - image: circleci/mysql:5.7
        environment:
          MYSQL_ROOT_PASSWORD: rootpw
          MYSQL_DATABASE: test_db
          MYSQL_USER: user
          MYSQL_PASSWORD: passw0rd
    steps:
      - checkout
      - run:
          name: Waiting for MySQL to be ready
          command: |
            for i in `seq 1 10`;
            do
              nc -z 127.0.0.1 3306 && echo Success && exit 0
              echo -n .
              sleep 1
            done
            echo Failed waiting for MySQL && exit 1 
      - run:
          name: Install MySQL CLI; Import dummy data; run an example query
          command: |
            sudo apt-get update
            sudo apt-get install mysql*
            mysql -h 127.0.0.1 -u root -prootpw --execute="use test_db;"
      - run:
          mvn test
```

Here we are using two docker images, `Java 8` and `MySQL` and according to the way circle CI is set up both the images are built on the separate containers. So, we have to wait for MySQL to start before running the project.

With `- checkout`, we are getting the latest code from the given branch. Then we are waiting for the MySQL to be ready. Eventually, we are running a few SQL commands to connect to the database. Lastly, we are trying to run the tests.

Just push this part of the code and it will run the tests for you.

### Test changes that I had to do.

The earlier written tests are good for local, and they work great when trying it on the local. But while running the tests on the CI, we have to test a little more.

#### Strategy for testing

In the single Test case I am going to test two APIs, one for creating the `A School` and then checking if the entry was created or not.

#### Changes required in configuration

Since on CI, we have to create the tables again and again we have to change the following in the `application-test.properties` file. Also, since we have changed the database name, we can change that configuration as well.

```
spring.datasource.url=jdbc:mysql://localhost:3306/test_db
spring.jpa.hibernate.ddl-auto=create-drop
```

#### Changes required in Test file.

According to the strategy change, we will change the way we write our test as well. This is how our updated test file looks like.

```java
package io.singh1114.springboottut;

import org.json.JSONException;
import org.junit.Test;
import org.junit.runner.RunWith;
import org.skyscreamer.jsonassert.JSONAssert;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.boot.test.web.client.TestRestTemplate;
import org.springframework.boot.web.server.LocalServerPort;
import org.springframework.http.*;
import org.springframework.test.context.ActiveProfiles;
import org.springframework.test.context.junit4.SpringJUnit4ClassRunner;

@ActiveProfiles("test")
@RunWith(SpringJUnit4ClassRunner.class)
@SpringBootTest(webEnvironment = SpringBootTest.WebEnvironment.RANDOM_PORT)
public class SchoolControllerTest {

    @LocalServerPort
    private int port;

    TestRestTemplate restTemplate = new TestRestTemplate();

    @Test
    public void testGetSchoolData () throws JSONException {
        HttpHeaders postHeaders = new HttpHeaders();
        postHeaders.setContentType(MediaType.APPLICATION_JSON);

        String requestJson = "{\"name\":\"School 1\", \"principle\":\"Mr. Charles\", \"address\":\"California\"}";
        HttpEntity<String> schoolPostEntity = new HttpEntity<String>(requestJson, postHeaders);

        restTemplate.exchange(
                createURLWithPort("/school"),
                HttpMethod.POST, schoolPostEntity, String.class);

        HttpHeaders headers = new HttpHeaders();
        HttpEntity<String> entity = new HttpEntity<String>(null, headers);

        ResponseEntity<String> response = restTemplate.exchange(
                createURLWithPort("/schools"),
                HttpMethod.GET, entity, String.class);

        String expected = "[{\"id\":1,\"name\":\"School 1\",\"principle\":\"Mr. Charles\",\"address\":\"California\"}]";
        JSONAssert.assertEquals(expected, response.getBody(), false);
    }

    private String createURLWithPort(String uri) {
        return "http://localhost:" + port + uri;
    }
}
```

Firstly, we are sending a `POST` request to the `/school` API to add data to the school database and finally we are sending a `GET` request to get the data for `/schools` API.

We can confirm that the things are working fine by running the tests in debug mode and stopping once the `POST` request is made and checking in the database at the same time. Once the test is done, you can run the same SQL command to see that the table was deleted.

{% include lazyload.html image_src="https://i.ibb.co/zb9CB2p/Screenshot-2020-04-24-at-1-21-29-AM.png" image_alt="Run Java Tests in Debug mode" image_title="Run Java Tests in Debug mode" %}

{% include lazyload.html image_src="https://i.ibb.co/LryGrDm/Screenshot-2020-04-24-at-1-23-39-AM.png" image_alt="Mysql DB select query" image_title="Mysql DB select query" %}

Finally you can push the code to see the tests running on CircleCI.

{% include lazyload.html image_src="https://i.ibb.co/5FLQ44M/Screenshot-2020-04-24-at-1-26-43-AM.png" image_alt="Tests passing on Circle CI" image_title="Tests passing on Circle CI" %}

You can learn more about the changes in the following Pull Requests.

[Circle CI setup PR](https://github.com/singh1114/java_tutorial/pull/1)

[Test changes PR](https://github.com/singh1114/java_tutorial/pull/2)

I hope you liked the post. Please share your views in the comment section below. Also, please [Subscribe](https://ranvir.xyz/blog/subscribe) if you want to read more such posts.