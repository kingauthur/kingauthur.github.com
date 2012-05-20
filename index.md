---
layout: page
title: Less is more，simple is elegance
tagline: Supporting tagline
---
{% include JB/setup %}




<div >
  {% for post in site.posts %}
    <p class="title">{{ post.date | date: "%m - %d - %Y" }}</p> 
    <p class="line"><a href="{{ BASE_PATH }}{{ post.url }}" class="title">{{ post.title }}</a></p>
    <p class="excerpt,line">{{ post.description }}</p>
  {% endfor %}
</div>



