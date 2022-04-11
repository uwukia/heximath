---
layout: default
title: "Posts by Tags"
---

<div style="height: 20px;"></div>

{% for tag in site.data.tags %}

<details>

{% assign posts_unsorted = site.blog_posts | where_exp:"item","item.tags contains tag" %}
{% assign posts = posts_unsorted | sort:"year" | sort:"month" | sort:"day" | reverse %}
{% assign count = posts.size %}
<summary style="cursor: pointer; margin: 4px;">
<b>{{ tag | capitalize }}</b>: {{ count }} post{% if count > 1 %}s{% endif %}
</summary>

{% for post in posts %}
<div style="display: flex; justify-content: space-between; padding: 2px; margin: 0px 4px;">
<div><a href="{{ post.url | relative_url }}">{{ post.title }}</a></div>
<div>{{ site.data.value_month[post.month] }} {{ post.day }}, {{ post.year }}</div>
</div>
{% endfor %}

</details>

{% endfor %}