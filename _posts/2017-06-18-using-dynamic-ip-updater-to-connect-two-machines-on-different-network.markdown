---
author: ranvirsingh1114
comments: true
date: 2017-06-18 22:51:41+00:00
layout: post
link: https://ranvirsinghprojects.wordpress.com/2017/06/19/using-dynamic-ip-updater-to-connect-two-machines-on-different-network/
slug: using-dynamic-ip-updater-to-connect-two-machines-on-different-network
title: Using Dynamic IP updater to connect two machines on different network
wordpress_id: 713
categories:
- Networking
---

From a few days, we are working on a problem which is related to reaching two machines that are connected to different networks. This post is the update to the earlier post in which we talked about the [installation of TightVNC](http://wp.me/p7kUg1-bn). In that post, we have talked about the problem that we are facing in lot detail. You can read it if you want to.

Now coming back to today's topic, like an amateur search engine user, I searched for a few random words that came into my mind about the problem. The search engine( Google), led me to [this post.](http://www.online-tech-tips.com/computer-tips/ddns-dynamic-dns-service/http://www.online-tech-tips.com/computer-tips/ddns-dynamic-dns-service/) This post explains properly about how the things work in the networking. I would like to summarise the things in a paragraph.

According to the post, for a machine connected to a network, there are two kinds of IPs. One is dynamic IP and other is static IP. Most of the systems have a dynamic IP which keeps on changing from time to time and other is static IP which doesn't change. Whenever we try to open up a website we either give the domain name of the website or we give the static of the server where the website is located. Now that system has a static IP which doesn't change. That is why we are able to access the website on the same IP. Our ISP( Internet Service Provider) keeps a list of the related domain names and IPs associated with them.

Also, it is cheaper for the ISPs to give a dynamic IP to the home computer than to provide a static IP( I don't know why). So they provide a dynamic IP to all the computer where their service is being used. Now to overcome this, some good people have created the concept of Dynamic DNS( Dynamic Domain Name Server). In this, a service is used which keep on telling the changing IP to the second machine that wants to connect to the first machine. In this way, the connection can be made easily.

Now the post gives out gives a few options for Dynamic DNS service providers but we love open source. Again I used the search engine to find a few open source dynamic DNS service provider.

After hours of searching and reading, I am able to figure out two things,



 	
  1. We need a client that is going to listen to the changes that are made in our IP and redirect the request to your IP to the new IP.

 	
  2. Another software that will stay on the computer and will share the changes in the IP with the client on the internet.


Redirection in the first software is handled by making use of a sub-domain. They provide you with a special domain name which can be easily reached. The IP will be taken care by them.( The subdomain will look something like yourusername.theirdomain.com)

I am able to figure out the first part. We are going to use another open source service called [nsupdate.info.](https://www.nsupdate.info)

The rest part in going to be figured out in the next post. Till then good bye.
