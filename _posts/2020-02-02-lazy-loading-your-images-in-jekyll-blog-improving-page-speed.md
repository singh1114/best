---
layout: post
title: 'Lazy Loading your images in Jekyll blog | Improving page speed '
date: 2020-02-02T15:51:44.081Z
description: >-
  Lazy loading the images of the blog and improving your page speed giving
  better user experience. Defer Offscreen Images in a Jekyll blog.
published: true
tags:
  - jekyll
  - blogging
  - seo
categories:
  - jekyll
  - blogging
  - seo
---
Images are the heaviest part of your blog and often are the most interesting once. The one things without which your post can't be complete.

Most of the people in a Jekyll blog tend to upload the images onto the directory on which the blog is hosted. Atleast such is the case with the people hosting it using GitHub pages.

If you check the pagespeed of your page on the [Google's pagespeed](https://developers.google.com/speed/pagespeed/insights/), you might have seen Google giving some suggestions related to images if your page contain a good number of images.

One of the major one is to **Defer Offscreen Images**, that is what we are going to do in this post.

## Introduction to the problem: Defer offscreen images

When your blog post has a lot of content and the people have to scroll to see the images of the content, then Google suggest to load the images after the whole [DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction) is loaded first.

> Deferring off screen images means delaying loading of images that appear below-the-fold on the page.

There are a lot of ways of doing [this](https://www.tezify.com/how-to/defer-offscreen-images/).

## Using Lazysizes

Before jumping into the tutorial, I want to state that if you follow this tutorial, you will have to change the way you define images in your Jekyll blog post, you won't be able to use the old `liquid` tags.

We are going to use [Lazysizes](https://github.com/aFarkas/lazysizes) to help us with the deferring of the offscreen images from the blog posts.

## Get the Lazysizes min file.

Lazysizes JavaScript `min` file can be found [here](http://afarkas.github.io/lazysizes/lazysizes.min.js). Just copy the content to a file named `lazysizes.min.js` and import it into the base file of your blog.

The best place to include it, would be in the `default.html`.

```
<script src="/blog/lazysizes.min.js" async=""></script>
```

## Giving a class to images in Jekyll

You can give the `lazyload` class to your images and get started with the library.

You can use the following code to add class to images in Jekyll

```markdown
![alt text](https:image/source.png "title text"){:class="lazyload"}
```

This is the first step to get started but we won't be using it. We will directly be adding this `class` to every image of all the posts on its own with new style.

## Creating a image creation script using the variables passed.

Write the following script and add it to the `_includes` directory so that you can include them from posts.

`_includes/lazyload.html`

```
{% if include.image_src %}
  <!-- If javascript is not on. -->
  <noscript><img src="{{include.image_src}}" alt="{{include.image_alt}}" title="{{include.image_title}}" /></noscript>

  <!-- If javascript is present. -->
  <img data-src="{{include.image_src}}" alt="{{include.image_alt}}" title="{{include.image_title}}" class="blur-up lazyload" />
{% endif %}
```

This script is checking if the `image_src` and javascript is enabled by the given client.

If yes, it uses the passed variables and renders an `image` with `data-src`( required by lazysizes to defer offscreen images). Otherwise, it will render a normal image.

## Include lazy loading in the posts.

While writing the posts you can include the newly created `lazyload.html`.

<script src="https://gist.github.com/singh1114/e5cfa80c4539fef26f2213f56b676e3e.js"></script>

That's it. After this you will not see the Google pagespeed's suggestion to defer your offscreen images.

## Changing the old images to follow the new script

I know changing the images in your earlier posts can be a pain, so I created this `python` script that can help you with that.

```python
ff = open('_posts/your_post.md')

for a in ff:
    # Check if the line contains markdown image tag.
    if a[0:2] == '![':
        alt = a[2:].split(']')[0]
        src = a.split('(')[1].split(' ')[0]
        title = a.split('"')[1].split('"')[0]
        print('{}{} include lazyload.html image_src="{}" image_alt="{}" image_title="{}" {}{}'.format('{', '%', src, alt, title, '%', '}'))
```

This will print the images tag following the new include statement. You can then copy them to the post.

If you directly want to update the old images with the new tags then you will write to the post file as well.

Thanks for reading the post. Do share your views.
