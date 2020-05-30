---
layout: post
title: Creating Maven based Spring Boot CI pipeline using CircleCI
date: 2020-05-30T15:10:30.507Z
updated_date: 2020-05-30T15:10:30.523Z
description: Setting up continuous Integration pipeline for maven based spring
  boot application using circleci.
published: true
tags:
  - java
  - springboot
  - testing
categories:
  - java
  - springboot
  - testing
show_ads: false
---
It is very important to automate the process of running the tests before deploying your code. [CircleCI](https://circleci.com/) is a good service which can help you to create [CI](https://en.wikipedia.org/wiki/Continuous_integration) pipelines for your project.

If you haven't yet set your test environment, you can do so by following my last post on Spring boot integration tests.

{% include linked_post.html url="testing-in-spring-boot-java-with-junit-for-beginners" %}

CircleCI will try to run the project according to the configuration specified in a special `yml` file.

## Login to CircleCI and turn on the test for the repository

You can easily log in to Circle CI using your GitHub or Bitbucket account. After that you can turn on the CI pipeline by clicking on `Set up Project` button for that repository.

{% include lazyload.html image_src="https://i.ibb.co/1MJd984/Screenshot-2020-04-24-at-12-52-04-AM.png" image_alt="Circle Setup Project" image_title="Circle Setup Project" %}

In the next step it will ask you about the language of the project. You can choose any and according to your choice it will create a branch with `.circleci/config.yml` file in the root directory.

After a lot of tweaks to the config file that CircleCI created for me, I ended up with this.

## .cirlceci file

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

## Test changes that I had to do.

The earlier written tests are good for local, and they work great when trying it on the local. But while running the tests on the CI, we have to test a little more.

### Strategy for testing

In the single Test case I am going to test two APIs, one for creating the `A School` and then checking if the entry was created or not.

### Changes required in configuration

Since on CI, we have to create the tables again and again we have to change the following in the `application-test.properties` file. Also, since we have changed the database name, we can change that configuration as well.

```
spring.datasource.url=jdbc:mysql://localhost:3306/test_db
spring.jpa.hibernate.ddl-auto=create-drop
```

### Changes required in Test file.

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

We can confirm that the things are working fine by running the tests in debug mode and stopping once the `POST` request is made and checking in the database at the same time.

{% include lazyload.html image_src="https://i.ibb.co/zb9CB2p/Screenshot-2020-04-24-at-1-21-29-AM.png" image_alt="Run Java Tests in Debug mode" image_title="Run Java Tests in Debug mode" style="text-align: left;" %}

Once the test is done, you can run the same SQL command to see that the table was deleted.

{% include lazyload.html image_src="https://i.ibb.co/LryGrDm/Screenshot-2020-04-24-at-1-23-39-AM.png" image_alt="Mysql DB select query" image_title="Mysql DB select query" style="text-align: left;" %}

Finally, you can push the code to see the tests running on CircleCI.

{% include lazyload.html image_src="https://i.ibb.co/5FLQ44M/Screenshot-2020-04-24-at-1-26-43-AM.png" image_alt="Tests passing on Circle CI" image_title="Tests passing on Circle CI" %}

You can learn more about the changes in the following Pull Requests.

[Circle CI setup PR](https://github.com/singh1114/java_tutorial/pull/1)

[Test changes PR](https://github.com/singh1114/java_tutorial/pull/2)

I hope you liked the post. Please share your views in the comment section below. Also, please [Subscribe](https://ranvir.xyz/blog/subscribe) if you want to read more such posts.