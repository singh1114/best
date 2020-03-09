---
layout: post
title: The problem of key distribution in symmetric keys
date: '2016-11-29T14:55:00.000-08:00'
author: Fierce Warrior
tags:
- cryptography and network security
- The problem of key distribution
- symmetric keys
modified_time: '2016-11-29T14:55:57.276-08:00'
---
The problem of key distribution is one of the most basic problems faced in the case of symmetric keys. As the
    name suggest there is a difficulty of key sharing in the case of symmetric keys. In the case of the symmetric key,
    there is only one key that is why it must be kept secure on the both ends.

    For explaining this we need to take an example of a receiver and a sender. The receiver and the sender want to have
    a communication using a key. So receiver says that he will generate the key. So the receiver generates the key and
    the same key needs to be with the sender for the encryption.

    Now the only option remains with the receiver is that he sends the key in the public and hopes that nobody out there
    is going to trap the key and read their future messages.

    One other option with the receiver is that he puts a key and encrypt this with another key and sends it to the
    sender. But this will not work as the sender does not have the key for the outer encryption.

    This problem in which there is no correct mechanism in place to share a symmetric key is known as the problem of key
    distribution.

    There are two known ways of removing this problem.

    * Diffie-Hellman algorithm for sharing keys.
    * Using both symmetric and asymmetric keys together. 
