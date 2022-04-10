---
layout: default
title: "Posts by Date"
---

{% assign years = site.blog_posts | group_by: "year" %}
{% assign yearsSorted = years | sort %}
{% for thisYear in yearsSorted reversed %}

{% for month in site.data.months reversed %}

{% assign thisMonth = thisYear.items | where:"month",site.data.month_value[month] %}
{% assign posts = thisMonth | sort:"day" %}

{% if posts.size > 0 %}
### {{ month }}, {{ thisYear.name }}
{% endif %}

{% for post in posts reversed %}

<div style="display: flex; justify-content: space-between; padding: 2px;">
<div><a href="{{ post.url | relative_url }}">{{ post.title }}</a></div>
<div>{{ site.data.value_month[post.month] }} {{ post.day }}, {{ post.year }}</div>
</div>

{% endfor %}

{% endfor %}

{% endfor %}