---
title: Integrity testing of APIs in Spring-Boot( Java) with Junit | For Beginners
date: 2019-10-18 22:48:00 Z
categories:
- java
- springboot
- testing
tags:
- java
- springboot
- testing
---

Shipping our product without testing is like selling a car without turning on the engine. We have to run a few tests again and again while the development of the product and if those tests are not automated, we will have a hard time to test our application.

I have written a post on the [importance of writing tests](https://singh1114.github.io/blog/writing-unit-tests-for-the-models/) against your codebase.

![Spring boot logo](https://i.imgur.com/BEIqT5f.jpg "Spring boot logo")

This post is in continuation of the last post we shared related to Spring boot in which we shared on how to write [Rest APIs in Spring Boot.](https://singh1114.github.io/blog/building-restful-apis-with-java-spring-boot-framework-for-beginners/). Please go through that post if you want to learn on how to create rest APIs using Spring Boot.

In this post, we are going to discuss how we can test our spring boot application from start to end without any mocking.

First of all, we have to add the `test` libraries to the `pom.xml`, so that maven can install them for us.

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

![Spring boot test passing](https://i.imgur.com/dyU6gXj.png "Spring boot test passing")

I hope you liked the post. Please share your views in the comment section below.