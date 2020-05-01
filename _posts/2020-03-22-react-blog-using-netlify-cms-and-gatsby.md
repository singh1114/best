---
title: Create react based blazingly fast blog using Netlify CMS and Gatsby
date: 2020-03-21T19:22:14.832Z
updated_date: 2020-03-21T21:54:28.482Z
description: Create awesome and fast react based blog using Gatsby and netlify
  CMS easily with Google Analytics, Redirects and setting up custom domain.
published: true
image: https://i.imgur.com/Dq9owl5.png
tags:
  - seo
  - netlifycms
  - gatsby
categories:
  - seo
  - netlifycms
  - gatsby
---
{% include lazyload.html image_src="https://i.imgur.com/Dq9owl5.png" image_alt="Create a React blog using Gatsby and netlify CMS" image_title="Create a React blog using Gatsby and netlify CMS" %}

I have been writing posts on [this blog](https://ranvir.xyz/blog) since a long time now and it has a long list of amazing post that you might want to read. Some weeks ago, my colleague shared the Gatsby blog that he created for his personal use.

Whenever I see a new website, I immediately head over to Google's pagespeed insight to find out the speed of the page. I was astonished by the speed that the page was able to achieve.

{% include lazyload.html image_src="https://i.imgur.com/UsKCfsh.png" image_alt="PageSpeed numbers for a React based Gatsby blog" image_title="PageSpeed numbers for a React based Gatsby blog" %}

Honestly speaking I was never able to reach to those numbers on [this blog](https://ranvir.xyx/blog).

If someone can help me with that feel free to [email me](https://ranvir.xyz/about).

So, I started working on my personal Gatsby blog. This post will contain all the details which I happen to do to make [that blog](https://blog.ranvir.xyz/) to the stage it is currently at.

## Final result

The final blog after this series is going to be [present on this URL](https://peaceful-mayer-ecb11a.netlify.com/).

## Prerequisites

I don't think there are any prerequisites required to start a blog using Gatsby and Netlify CMS, It is fairly easy to set up if you know how to make changes and use basic GitHub.

The basic things required for this specific version of post are:

### Domain Name

I already had a [domain name](https://ranvir.xyz) which I was already using. It will still work if you don't have one though. 🙏

### GitHub Account

To follow this tutorial, you will need to have a GitHub account where the code for the blog can reside. There are other ways to keep the code, but I think GitHub provides the easiest way to maintain your code.

We are using it because I have been using it for long time, otherwise you most probably use any other Code Hosting platform without any problem.

### Netlify Account

You will also need account on [Netlify](https://www.netlify.com/) so that you can deploy your blog. 

The rest of the stuff we are going to figure out during the course of the post.

Let's begin.

## Choose a theme

You can choose from a list of themes that are available. Most of them has `deploy on Netlify` button which will deploy it directly on Netlify and can save the code to your Netlify servers and GitHub Account. Next time you make any change to your code, netlify will automatically detect the change and deploy the change.

{% include lazyload.html image_src="https://i.imgur.com/Ag2ERnJ.png" image_alt="Deploy Gatsby blog on Netlify using GitHub" image_title="Deploy Gatsby blog on Netlify using GitHub" %}

I choose the basic [gatsby-theme-blog](https://www.netlify.com/with/gatsby/). Just click on the deploy button and choose `Connect to GitHub`. Finally, choose the name of the Repository that you want to contain the code in. The code will host on the given GitHub repository.

## Making the changes

Once your site is deployed on `something.netlify.com`, you can clone the code locally and start making the changes.

```shell
git clone https://github.com/your_repo/repo_name
```

For more information on various [git commands check this post](https://ranvir.xyz/blog/basic-commands-in-github/).

The first thing to change is in the `gatsby-config.js` file. Change `siteMetadata` as follows

```javascript
  siteMetadata: {
    title: `Tutorial blog`,
    author: `Ranvir`,
    description: `Basic description of the blog`,
  ...
```

Push the code and you will see the changes being deployed in your Netlify account. `https://app.netlify.com/sites/your_site_id/deploys`.

{% include lazyload.html image_src="https://i.imgur.com/ACODtqR.png" image_alt="Changes to GitHub code deploys blog on Netlify" image_title="Changes to GitHub code deploys blog on Netlify" %}

```bash
git push origin master
```

After some time the changes will be available on the current website.

## Adding Netlify CMS

Adding Netlify CMS will help you to quickly make changes to your posts and deploy them with a click of a button. All your posts are at a single place.

You can create and edit your posts easily using the Netlify CMS.

For adding Netlify CMS and allowing editing using GitHub Login, you will have to add a `static` directory to the root of your code.

Add this to the `static/admin/config.yml` file.

```yml
backend:
  name: github
  repo: singh1114/tutorial
  branch: master

media_folder: static/img
public_folder: /img

collections:
  - name: "blog"
    label: "Blog"
    folder: "content/posts"
    create: true
    slug: "{{slug}}"
    editor:
     preview: false
    fields:
      - { label: "Title", name: "title", widget: "string" }
      - { label: "Publish Date", name: "date", widget: "datetime" }
      - { label: "Image", name: "image", widget: "string", required: false }
      - { label: "Tags", name: "tags", widget: "list", required: false }
      - { label: "Description", name: "description", widget: "string" }
      - { label: "Body", name: "body", widget: "markdown" }
```

You can change the fields using [widget guide](https://www.netlifycms.org/docs/widgets/) according to your needs.

After deploying this you can access the website's admin panel on `https://web.netlify.com/admin`.

For turning on the GitHub login on your website's admin page, so that only you can edit the posts, you will have to turn on the OAuth access using your Netlify account.

Just go to the `settings tab > Access Control > OAuth >Install Provider`. For installing, you will need auth credentials which you can generate using the [GitHub Application page](https://github.com/settings/applications/)

Add your netlify address as the home page URL and `https://api.netlify.com/auth/done` as callback.

Once done, you will be able to Login to the admin panel and make changes to the posts directly.

{% include lazyload.html image_src="https://i.imgur.com/CEM2fBI.png" image_alt="Admin panel for Gatsby blog on Netlify CMS" image_title="Admin panel for Gatsby blog on Netlify CMS" %}

## Adding Redirects

As I already told you that I had a domain name and I wanted the website to be hosted on that `https://blog.ranvir.xyz` and not on `something.netlify.com`. For this you can set up `CNAME` record in your domain name provider DNS management.

You can find more about what record to set with simple google search.

In my case, where I was using a subdomain, I had to use `blog` as a host and `something.netlify.com` as value.

After that is done you can redirect, `something.netlify.com` to `blog.ranvir.xyz` by creating a redirect file.

Create `static/_redirects` file and add the following content to it.

```
# Redirect default Netlify subdomain to primary domain
https://something.netlify.com/* http://blog.ranvir.xyz/:splat 301!
```
 
This will create a `301` permanent redirect.

## Adding Google Analytics

Adding analytics to your website can be very useful, you can check how many people are looking at your website at every given moment.

You just have to install a basic `npm` package and add the Google Analytics tracking ID to your code.

```bash
npm install --save gatsby-plugin-google-analytics
```

Now change the code in the config file.

```javascript
module.exports = {
  plugins: [
    ...
    {
      resolve: `gatsby-plugin-google-analytics`,
      options: {
        trackingId: 'UA-*******-*'
      }
    },
    ...
```

You can take the tracking ID from the Google Analytics dashboard.

Hope you liked the post. If you did please share with your friends.
