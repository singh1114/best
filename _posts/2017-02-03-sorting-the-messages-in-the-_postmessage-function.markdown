---
author: ranvirsingh1114
comments: true
date: 2017-02-03 10:06:06+00:00
layout: post
link: https://ranvirsinghprojects.wordpress.com/2017/02/03/sorting-the-messages-in-the-_postmessage-function/
slug: sorting-the-messages-in-the-_postmessage-function
title: Sorting the messages in the _postMessage function
wordpress_id: 623
---

I am trying to sort the messages that I am receiving when I used the getHistory function in the Message Archiving. But till now I haven't found a success.

They say failures are the greatest teachers. I hope they are true because yet again, I have failed.

A lot of tough words up there. Let's simplify the situation a little. So from last few posts, I have been talking about XMPP- The protocol for chatting( or message sharing). I did posted them because I was working on a chatting web-client called JSXC. I tried it and found that the client never retrieved messages from the server. So my work was to implement this feature.

With the help of the main developer, I was able to make some progress and made the messages appear into the chat box. As the developer told me that the messages are not going to be sorted so I have to make some changes in the function such that the sorted messages can appear in the chat window.

In this post I want to discuss the way in which I wrote the function without showing the real code so that we can keep everything simple. First of all, I wrote the getHistory function such that if there is message in the server for a particular person( we call it jid in terms of XMPP), make a object having everything about the message and send it into the function named postMessage which in return is responsible of printing these messages into the chat box.

Now, I did checked personally that the messages are stored properly on the server and they are retrieved properly one at a time. Whenever a message is retrieved from the server the message is given to the function for printing. But to my surprise the messages order does not remain intact and messages printed in the chat box are in no particular order.

So I decided to make some changes to my function. I changed the function and now the function saves all the messages for a partcular person in an array and when all the messages are retrieved they are sent to the function for printing. I used a loop to make it work but as far as I think it is not working. I don't know why.

For more details stay tuned. Also this week was great in terms for my typing speed. I wrote whole of this post without giving a single look to the keyboard. Also the speed have reached a new level of 30 wps. Which is a great progress.
