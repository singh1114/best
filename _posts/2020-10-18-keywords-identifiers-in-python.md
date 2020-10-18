---
layout: post
title: Second part of series
date: 2019-02-13T08:42:00.000Z
updated_date: 2019-02-13T08:42:00.000Z
description: Second part of series
published: true
categories:
  - python
  - beginners
author_name: Ranvir Singh
author_username: ranvir_xyz
show_ads: false
show_telegram_signup: false
series_unique_code: python_beginner_series
series_part: 2
series_page_title: Keywords and Identifiers
series_title: Python Introduction
---
Second part of series

python, django, webdev

Second part of series

python, django, webdev

Second part of series

python, django, webdev

Second part of series

python, django, webdev

Second part of series

python, django, webdev

Second part of series

python, django, webdevSecond part of series

python, django, webdev

Second part of series

python, django, webdev

{% for post in site.posts %}
    {% if post.author_username == "ranvir_xyz" %}
        <div class="linked_post_div">
            <article class="post">
                <h3><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h3>
                <p style="color: #969494; margin: 10px 0px; font-size: 18px;">
                    {% for category in post.categories %}
                        #{{ category }}&nbsp;&nbsp;
                    {% endfor %}
                    <br><br>
                    {{ post.date | date: "%B %e, %Y" }}
                    {% include read_time.html content=post.content %}
                </p>
            </article>
        </div>
    {% endif %}
{% endfor %}