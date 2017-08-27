---
author: ranvirsingh1114
comments: true
date: 2017-01-13 07:50:06+00:00
layout: post
link: https://ranvirsinghprojects.wordpress.com/2017/01/13/some-features-of-xmpp/
slug: some-features-of-xmpp
title: Some features of XMPP
wordpress_id: 561
categories:
- JavaScript
---

Hello guys,

Welcome back to another exciting blog post on this blog. I hope after reading this post, you will be very excited to work in the field XMPP. Long ago developers used a lot of their important time to write the chatting applications. That was the time when they used the HTTP protocol to write those apps. But the time had changed for good and we found something good as the alternative known as XMPP.

XMPP stands for "Extensible Messaging and Presence Protocol". As the name suggests, it is the protocol that is used to make the chatting applications. The protocol makes it so easy to create a chatting application. In XMPP all the features are divided into XEP's. I don't know the full form of this and I am very lazy to type it in the GOOGLE. But I am sure if you want to you can google it. For example, if you want to implement a chatting application with a feature of Multiple Users in a room( Modern day applications call them groups) then you can find a page on the XMPP website and you can open the page.

**xmpp**.org/extensions/xep-0045.html.

For every small feature that you can think of is given a name and a number in the XMPP. When you go through these pages you will learn the way in which the chatting applications works.

I can write the whole specs about the XMPP up here. But, I am sure that I will not be able to explain as well as this great developer JACK MOFFITT did in this video.

https://www.youtube.com/watch?v=WktC6vc4WQs&t=1221s



Jack Moffitt also wrote the book on XMPP which is a great read. If you want it you buy it on the amazon. I will sum up some of the basic things discussed by the developer in the video. I have not explained about the concepts like long polling and some more as the video explains it all.

In XMPP the connection is made with the help of JID and a password.



	
  * JID are divided into two categories, bare JID and full JID.

	
  * Full JID is like darcy@pemberley.lit/library.

	
  * Bare JID is like darcy@pemberley.lit

	
  * Messaging is done with the help of stanzas. Stanzas are the basic sending and receiving method in the case of the XMPP. If you want to know something about a JID on the network send a stanza to the server and server will respond with the answer.

	
  * Stanzas are divided into three parts on the basic level. These are:



	
  1. Presence

	
  2. message

	
  3. IQ



	
  * Chatting is a two-way process. It includes the message to be transferred from the client to the server and server sending back the response.  So this set of XML is known as a stream.


If I missed some basic point do write in the comments below.

Now XMPP made our life easier by writing down everything and specifying everything properly. But, that was not enough as the protocols are not enough if you want to build something on the top of the protocol you have to cover a lot of stuff.

For example, let's say you are writing a chatting application and you start from scratch. Then you have to implement more than 300 small protocols to make the chatting applications. So the great developers like Jack came up with the idea to build something on the top of the protocol and make the procedure easier for the developers who want to implement their own chatting apps. This was the reason that brought the **strophe.js** library into the picture.

All those developers spent day and night to come up with a simple interface that can talk to the server and the client with the help of mere functions.

I have already tried a lot of chatting applications out there because I did not wanted to start from the scratch. As we all know it a very difficult task in the beginning as you are very new to all the concepts in the code. But as you start grasping the code you come to know what is happening.  Now, this may take time according to how much you already know about the framework and the language.

Now all the clients were built in JavaScript as we wanted to implement the web client. As you guys know that I have been writing the JS code for a long time but still there was something odd about this code. They used namespaces and something called the combination of object-oriented and functional programming.

So this is forcing me to learn the functional programming. So I read a lot of posts and books about this and trust me it went right over my head. All those concepts like Fuctors,  monads etc were the terms that I had never heard. So I tried to skip that part and come back to it in a while. But all those concepts can be said to be interesting.

That is the story for another post. For now, I am trying to implement the Message Archive Management into the JSXC web client. I am in the conversation with the developer of the JSXC who is helping a lot from a few days. Let's hope that I can add a prototype in the main repo so that we can use this web app.

Here is the github link to the developer of the JSXC who has bee  helping a lot. Do check him out.

https://github.com/sualko

Thanks for reading. Do like the post and Happy coding.


