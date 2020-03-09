---
layout: post
title: Usage of symmetric keys and asymmetric keys in encryption
date: '2016-11-29T14:34:00.000-08:00'
author: Fierce Warrior
tags:
- cryptography and network security
- asymmetric keys
- The problem of key distribution
- symmetric keys
- Diffie-Hellman algorithm
modified_time: '2016-11-29T14:34:00.400-08:00'
---
Let's visualise the time when the internet just started and the people were started getting hold. Of course,
    this was the time when the US military made the internet public. Everyone was fascinated by the new thing. So you
    can reach anyone who is miles away just by using a service called the internet.

    As the usage of the internet started increasing the people who were influenced by it started increasing. They
    started sharing important data with each other and started creating a mess all over the internet. Some other people
    who were technically skilled and watching everything took the advantage of the situation and started using this
    information for their own use.

    These technically skilled people are known as intruders in the technical language. Now everyone was getting shocked
    by one or two attacks on them. So the body who ran the internet decided to come up with the idea to make the
    internet more and more secure. They asked everyone out there to create something that can help to improve the
    situation.

    All these algorithms were based on the substitution and transformation
    methods to create the cipher
    text( encrypted form of the message). But before knowing the various algorithms(Methods of creating algorithms) we
    should know some basic things that were included in these algorithms.

    In this post, we are going to discuss the about something about the keys. What are the keys, What are the types of
    keys, and what are need of the keys? This is all that we are going to discuss in the post. I hope this post will not
    be very big.

    So keys are some fixed set of characters that converts the simple message( Plain text in technical terms) into the
    cipher text( encrypted text) so that anybody can see the message that is being sent but should not be able to
    understand what is written inside it. When the legitimate user receives the message, he/she uses the same key to
    decrypt the message and read the message.

    Now you might be trying to guess how can we convert the message into the encrypted text by making use of this set of
    characters called keys. So basically this is cryptography. We are going to discuss some algorithms that can do our
    job. We will discuss all of them in detail in coming future.

    Now let's talk about the types of keys. So, there are two types of keys namely,

    * Symmetric keys
    * Asymmetric keys

    In the case of the symmetric key, there is only one key. Both the sender and receiver, both have the same key. This
    key is used for both the operations of encryption and decryption. The encryption process by making the use of this
    key is very fast. But there are something disadvantages of this one of which is known as The problem of key
    distribution. This problem
    can also be solved by using
    Diffie-Hellman algorithm or by
    using both symmetric keys and asymmetric keys together.

    On the other hand, asymmetric keys consist of a set of keys. There is a public key and there is a private key for
    all the people who want to receive a message using this technique. First of all the person who wants to receive some
    text from the sender will withdraw two keys from the authority that provide the keys. One key is known as the public
    key and the another one is known as the private key. The public key is shared with everyone. Whenever a sender wants
    to share the message with that particular user then he/she uses the public key of the receiver to encrypt the text.
    Once encrypted this message can only be encrypted by the receiver's private key. Not even the public key can open it
    up.

    Now this type of encryption will take time. But it is more secure and widely used for higher encryption.

    There are some points that are worth of discussing one of which is the number of keys. Say I want to send a message
    to some people with some sensitive information in it. It might be the work of the company in which I work. It is
    very important to hide this information from our competition.

    If I take the symmetric key route then I have to generate a separate key for each and every receiver differently and
    send them the message differently. Now there will be a lot of keys accommodated at my end making it a cumbersome job
    to map them with the receivers. Also, I have to keep all the keys secure and not allow a intruder to reach the keys
    otherwise he/she will be able to listen to the communication. Whereas if I choose the asymmetric key route then
    every receiver will share their public keys and I will generate the encrypted text and send them off to the receiver
    where they will be decrypted.

    I hope I was able to convey myself. Please share this post and leave a comment below.
