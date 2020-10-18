---
title: Prashant Sharma
permalink: "/sharma_pacific/"
layout: post
---

![Profile Image](https://sharmapacific.in/assets/images/PrashantSharma.jpg)

Greetings! My name is Prashant,

An Engineering professional with 3+ years of experience in Software development.

He is a Post-graduate in CS from National Institute of Technology Calicut.

[Contact Him](mailto:sharma.pacific1@gmail.com)

[Website](https://sharmapacific.in/)

{% for post in site.posts %}
    {% assign page_slug = page.url | replace: "/", "" %}
    {% if post.author_username == page_slug %}
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
