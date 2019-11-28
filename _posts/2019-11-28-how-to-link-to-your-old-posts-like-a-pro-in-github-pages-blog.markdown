---
title: How to link to your old posts like a pro in GitHub Pages blog
date: 2019-11-28 18:10:00 Z
categories:
- jekyll
- beginners
- githubpages
tags:
- jekyll
- beginners
- githubpages
---

Linking to your old posts is very good for the SEO of your blog and help you not to write the same things again and again. It also helps you to interconnect to your old posts increasing the traffic to your website.

After writing a good amount of posts on [dev.to](https://dev.to/singh1114), I started liking the options they provide to share the old posts or other dev.to posts in a well-formated way.

I wanted to create the same experience on my personal blog as well.

As I use GitHub Pages ( Jekyll) to build my blogging website, I was sure that it won't be a huge task to do this.

![Dev to linking to posts](https://i.imgur.com/H1tqz8l.png "Dev to linking to posts")

I have a lot of separate widgets in this blog. When someone clicks on any of the posts, all these widgets come together and are shown to the user as a single unit.

Some examples of these widgets are:

### Social sharing buttons

The social sharing buttons on this page are included as a separate widget. This helps your readers to share your posts on social media.

BTW, please share this post on any of the social media and help us get more readers.

### Read time widget

The read time for any post on this blog is again a separate widget. I use it to show the amount of time it will take to read the post.

Now that we know how widgets work in Jekyll blog, let's try to create something similar to what dev.to have.

## Final result after creating 

Let me a link to the social sharing post that I created some time back to show you how the final result will look like.

{% include linked_post.html url="why-and-how-to-add-social-sharing-buttons-on-your-jekyll-blog-using-github-pages" %}