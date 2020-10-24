---
title: About
permalink: "/about/"
layout: page
---

Wide range of Python tutorials by our great authors.

---

### Best Blog Theme

`Best` blog theme is inspired by [Barry clark's Jekyll Now](https://github.com/barryclark/jekyll-now) and few inspirations
taken from other blogs as well.

There a lot of features in the blog. Each feature is a separate blog post available.

{% if site.show_authors %}
---

### Our Authors

<div class="original_source">
  {% for author_page in site.authors %}
    <div class="linked_post_div" style="margin: 10px 0px; font-size: 14.5px;">
      <article class="post">
        <h3>About Author &middot; <a href="{{ author_page.permalink }}">{{ author_page.title }}</a></h3>
        {% if author_page.description %}
          {{ author_page.description }}
          <br>
        {% else %}
          {{ author_page.excerpt }}
        {% endif %}
      </article>
    </div>
  {% endfor %}
</div>
{% endif %}