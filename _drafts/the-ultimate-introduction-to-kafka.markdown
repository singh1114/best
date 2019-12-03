---
title: The Ultimate Introduction to Kafka
date: 2019-12-03 17:42:00 Z
---

Apache Kafka is an Open-source asynchronous publish-subscribe messaging system that can help you build any of the offline task handling system, streaming service or any other data pipeline service.

## History of Kafka

Kafka was originally built at LinkedIn and was later open-sourced and donated to Apache Software Foundation. It is basically written in Scala. It is being used by all the top companies out there like Twitter, Airbnb and many more.

Other tools in the same domain at that time were giving high latency for the event data being passed and consumed by the services. The folks at LinkedIn wanted to build a tool that can replace the already existing non-scalable version of the data processing pipelines and create something that handles high scales.

## Introduction to Kafka

According to the official documentation of [Kafka](https://kafka.apache.org/intro), it is a distributed streaming platform and is similar to a enterprise messaging system.

### What is a simple messaging system?

A simple messaging system consist of 3 main parts.

1. **Producer**

A producer/ publisher is the part of the system which produces the messages. A message can be anything. Mostly there is a limit to the size of the message that a producer can produce and with the broker.

**For SQS the upper limit of the size if 256 KB**.

2. **Broker**

A Broker is an interface/ intermediate are the receivers of the messages. They store the messages for some time and pass it on to the consumers for further usage. In most of the brokers, there is a limit on till when you can store the message on a broker.

**For SQS the limit is 15 minutes whereas in Kafka the messages can stay for a longer time which can be configured according to the requirement.**

3. **Consumer**

The consumer is the part of the application which consumes the messages passed on by the broker. The consumer can handle the messages accordingly.

This simple setup can be used to handle log shipping to S3 or sending notifications to the customers.

**Image of everything**

This simple setup seems to solve small problems when the number of messages being consumed daily is somewhere below a few thousand. But once your application starts growing you will start facing the latency issues in the setup. The messages will be consumed at a slower rate leading to more messages in the queue at any given time.

As the number of producers increases, this kind of combination is hard to maintain and your broker becomes the bottleneck for your solutions to provide real-time solutions to your customers.

**Image here**

The basic Kafka features help us to solve all the problems that the other queue systems had at that time.

## The main feature of Kafka are:

1. It allows the saving of the messages in a fault-tolerant way by using a Log mechanism storing messages in with a timestamp.
2. It is distributed so if one of the nodes fails, your messages are still safe at some other node.
3. It processes messages as they occur by using the timestamp which is saved along with the message.
4. It provides both the features of the queue and producer-consumer architecture i.e. You can send the messages to a group of consumers in which case only one of the consumers will get the message or you can send it over to all the consumers.

## Architecture of Kafka

## Terms used in Kafka

## How to install and use Kafka

## How does Kafka handles failure

## Configurations available in Kafka

## Creating a producer and sending message to the broker

Handling callbacks of the messages sent.

## Consuming the message

