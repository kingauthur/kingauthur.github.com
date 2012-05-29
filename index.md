---
layout: index
title: Less is more，simple is elegance
tagline: Supporting tagline
---
{% include JB/setup %}




<div id="category">
  {% for post in site.posts %}
    <p>
    	<span  class="date">{{ post.date | date: "%m - %d - %Y" }}</span>
    	<span  class="title"><a href="{{ BASE_PATH }}{{ post.url }}" class="title">{{ post.title }}</a></span>
    </p> 
    <p class="desc">{{ post.description }}</p>
  {% endfor %}
</div>



