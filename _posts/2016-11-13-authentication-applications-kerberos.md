---
layout: post
title: 'How does kerberos authentication works: Authentication applications'
date: '2016-11-13T10:39:00.000-08:00'
author: Fierce Warrior
tags:
- Authentication applications | Kerberos | Cryptography and networks sercurity
- cryptography and network security
modified_time: '2016-11-29T13:15:17.334-08:00'
---

Today we are going to discuss some of the application of the authentications systems. These are the applications of the
authentication where the user is identified differentely and various services are provided to the user. Authentication
also helps in keeping a seprate user experience for every authencated user and working for each user with different
stratergy.

First of all we are going to discuss about one of the important authentication application that is widely used in the
servers running on windows environment. Yes we are talking about kerberos.

Kerberos uses a ticket system where ticket is used to identify the user integrily.

Some applications of kerberos include web authentication, signing in into a server and using various services provided
by the server.

Now while working with kerberos two type of tickets are generated

* Ticket-granting ticket: This ticket identifies the user globally and defferntiate the other users form this specific
user
* Service ticket: This ticket allows the user to get a particular service from the server for a particular amount of
time.

For eg: When a user log in to the a website then a TGT will be generated and further if he wants to access a particular
service he can get another ticket for that special service.

Now these tickets sometimes have a time limit which ends up after a particular amount of time.

**Servers**
There are two requirements here:

First of all. we want the users to get authenticated and at the same time we want the users to have the ticket for some
special treatment.

To accomplish these two tasks kerberos server uses a trusted third party service that does the work for them.

* Now the part doing the authentication is called **authentication server.**
* The part providing the tickets are called **Ticket granting server. **

A separate database is kept for keeping the secret keys of all the users and nothing is kept on the user side for
    the security purposes. 

**The authentication process**

The authentication is a three step process in the case of kerberos.



    * The client server( user) authenticate to the authentication server by requesting for the service along with the
    keys. In the return authentication server gives back Ticket-granting session key and ticket itself which will be
    used in the next step with the Ticket Grating server.
    * After this the client server authenticates itself to the Ticket granting server with the stuff that it received in
    the earlier process. In the result the TGS gives back the items that are required by the client server to get its
    hands on the services that it wants to explore on the server.
    * In the final step with the items that it received in the last step and make use of the various services till the
    expiration is achieved. 



**Advantages**

* Can work fine on even an insecure network.
* As all the processes are done under the shed of a secret key the attacker cannot attack and make use of the services.
* It is computationally efficient because of the use of symmetric key.
* It is Open-source.

**Disadvantages**

* If the third party doesn't function properly then the whole system shatters.
* If third party have less security then the data of users is at risk.
* As time stamps are used so everyone involved should have synchronized clocks.

