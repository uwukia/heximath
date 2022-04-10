---
layout: default
title: "Posts by Date"
---

{% for tag in site.data.tags %}

### {{ tag | capitalize }}

{% assign posts_unsorted = site.blog_posts | where_exp:"item","item.tags contains tag" %}
{% assign posts = posts_unsorted | sort:"year" | sort:"month" | sort:"day" | reverse %}
{% for post in posts %}

<div style="display: flex; justify-content: space-between; padding: 2px;">
<div><a href="{{ post.url | relative_url }}">{{ post.title }}</a></div>
<div>{{ site.data.value_month[post.month] }} {{ post.day }}, {{ post.year }}</div>
</div>

{% assign maxPosts = 5 | plus: 1 %}
{% if forloop.index == maxPosts %}
    {% break %}
{% endif %}

{% endfor %}

{% endfor %}