---
title: How to add inline Ads in Jekyll blog
date: 2019-10-30 17:05:00 Z
published: false
categories:
- Jekyll
- Blog
- Technology
tags:
- Jekyll
- Blog
- Ads
- Technology
---

With the coming of new blogging tools like [dev.to](https://dev.to) and [medium](https://medium.com). People tend to post mostly on those websites. But owning a separate blog on GitHub using Jekyll can give you a lot of freedom. You can do whatever you want with it.

While this issue is controversial, there is nothing wrong to monetize your work. If you love to write and blogs (like I do) you can add ads to your blog. Maybe you have launched a course and want to publicize it to your readers.

Although adding ads to might increase the bounce rate but we will add them in such a way so the user experience is not hindered.

I only have Google ads on this blog. Earlier the ads were placed on the sidebar and at the end of the blog.

A few days ago, I was thinking about how can I copy other blog strategies who show inline ads in-between the post and improve the CTR of the ads.

In this blog, we will try to add ads in-between the post content.

## Strategy for adding inline ads in Jekyll blog

The strategy here is pretty simple, we want to show a Google ad after every `ten` paragraphs of the content.

For accomplishing this, we will have to concentrate on the file, `_layout/post.html`

Here is the old content of the file.

<script src="https://gist.github.com/singh1114/ab15bb136a32c0724f9a861d375a9c52.js"></script>

`29`th line the most important line and is responsible for showing the content of the post.

## Adding inline ads in Jekyll blog: Tech Strategy

* Split the blog content on the basis of `<p>` tags.
* After every 10 Paras, add an ad.

Here is the code with that change

<script src="https://gist.github.com/singh1114/46164f4d478a1be063c2ee4636357f52.js"></script>

On the 4th line, we split the `content` variable using `<p>` tag and assigned it another variable `content_para`.

Then we are looping over this `content_para` and start printing it one by one.

Inside each loop, we are checking the loop index and finding its `modulo 10` which will give its remainder value and assigning the value to a variable `para_number`.

The value of `para_number` will be 0 when loop index is multiple of 10 i.e. 10, 20, 30 and so on.

You can add whatever you want to in the place. If you want to publicize your new course, you can do it.

That's it for today, I hope you liked the post. Please share it with your friends.

Also, it would help us if you leave a comment and appreciate if this helped you.

Also, if you have some doubt feel free to reach out using the comments section.