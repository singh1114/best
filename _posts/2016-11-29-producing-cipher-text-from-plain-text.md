---
layout: post
title: Ways of producing cipher text from plain text
date: '2016-11-29T13:35:00.001-08:00'
author: Fierce Warrior
tags:
- plain text
- cryptography and network security
- Network security techniques
- cipher text
modified_time: '2016-11-29T13:35:25.562-08:00'
---

    As we have discussed in one of my another post that a cryptography is the way of producing encrypted text out of the
    simple or plane text. In that post we also talked in detail about the defination of cipher text and plain text.

    So in this post we are going to discuss the ways in which we can convert the simple plain text to cipher text. I am
    sure I will we able to keep this post more user friendly such that non-technical people can also read it easily.

    I beleive that anything that is introduced into the stream of computer science are taken from the real world
    applications. So I will try to relate evrything to the real world examples.

    So after the first example we are definetely going to know the difference between the plain text and the cipher
    text. So let us start the journey.

    So the process of conversion of cipher text into plain text is divided into two parts, which are as follows.

    * Subsititution
    * Transposition

    Probably in this post we are only going to discuss about only a few of the substitution techniques and for the
        other one's you might like to read the follow ups.



        * **Ceaser cipher**

        Ceaser cipher is the one of the oldest techniques in which the every character in our message was replaced
            by a character that is a fixed distant far from the particular character. For exmaple, if we want to convert
            tech zodiac into the encrypted form than we will use the letters that are 3 forward from the character in
            the plain text.



    plain text : techzodiac

    cipher text: whflcgmdf

    Now this was not very difficult to crack but this is how it started. 

        * **Modified ceaser cipher **

        In this technique we converted the text such that the every charcter is not a fixed distance far i.e.
            earlier it was fixed to 3 but now the cipher text generator can keep it how much he wants. Thus the
            cryptanalyst( The one who tries to find the real text from the cipher text has to )



