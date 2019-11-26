---
title: 'Caching: Saving extra database calls and making your application faster'
date: 2019-11-26 21:16:00 Z
---

Caching is a way of stopping the server from hitting some time taking resource and sending the data before hitting that time taking resource. In most of the cases, these time taking resources are databases. This helps to improve the user experience by delivering stuff faster to the users.

Caching is not straight forward. You will have to design your caching strategies in a way such that users are not served some old data and at the same time your servers are not facing some unnecessary load.