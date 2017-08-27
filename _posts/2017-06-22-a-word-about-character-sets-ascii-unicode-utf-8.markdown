---
author: ranvirsingh1114
comments: true
date: 2017-06-22 12:06:17+00:00
layout: post
link: https://ranvirsinghprojects.wordpress.com/2017/06/22/a-word-about-character-sets-ascii-unicode-utf-8/
slug: a-word-about-character-sets-ascii-unicode-utf-8
title: A word about character sets - ASCII, unicode, UTF-8
wordpress_id: 798
categories:
- GSoC-2017
---

Let's talk about everything as it happened in the history. It was the time when UNIX was being built. ASCII came into the existence at that time. More such features were used before that but they are not being used now so talking about them is not valid anymore.

**ASCII:**

So the first thing that was useful and still being used is ASCII. This format used 8-bit space to store a character. So, we had 256 places to store everything. ASCII made a standard that assigned all the characters from 1-128. After that, the places were used by the people as they liked it. It was being used differently by all the people in different countries. This made difficult to send stuff from one country to another. The stuff sent by the person in one country was interpreted differently by the other countries.

Say, 129 is defined as some character in Greece. When this text is transferred to other place and they have defined some other character for 129, the text will change to that as we know when the text is transferred, it is transferred in the binary format.

**Unicode:**

This led to a problem which was needed to be solved quickly. At the same time, the internet started it's journey and it was becoming difficult to everyone. This time the Unicode came into existence. Another misconception in the mind of people is that Unicode stores everything n 16-byte characters and there is a limit to the number of characters that can be stored in Unicode. But it is not true. Unicode uses the concept of code point. Code point is a magic value that is assigned to every character that exists in the world. Like U+0048 for H. Here U+ stands for Unicode and the number is a hexadecimal number.

In memory, they are stored differently. They are stored in the group of two bytes each. Like H is stored as

00 48

e as

00 65 and so on.

That's why the misconception of 2 bytes storage came into existence. This looks good but they had a problem. The number stored as 00 48 can also be stored as 48 00. This happened because the early computer either used high to the low memory storage or low to high memory storage and the guys who implemented Unicode wanted to make it fast for both the people. So they had to reserve some bits where they can tell what type of encoding to be used which was either FE FF and FE FE.

Now the guys who wanted to store their stuff in the minimum space came to fight this new thing as most of the stuff they did usually use the letters in the English language so they will have more number of zeroes in the text when saved in the memory. This increased their total size. All these things lead to the birth of UTF-8

**UTF-8:**

UTF-8 used the simple concept. It had no limit on the number of bytes in which characters were being stored. And they also included the ASCII format so there was no wastage of space and when new characters started coming into existence, they were assigned some new codes.

This is the way things work in the field of character sets.

BTW Thanks for reading.
