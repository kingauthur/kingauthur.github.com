---
layout: index
title: Less is more，simple is elegance
tagline: Supporting tagline
---
{% include JB/setup %}




<div id="category">
  {% for post in site.posts %}
    <div class="item">
    <p>
    	<span  class="date">{{ post.date | date: "%m - %d - %Y" }}</span>
    	<span  class="title"><a href="{{ BASE_PATH }}{{ post.url }}" class="title">{{ post.title }}</a></span>
    </p> 
    <div class="content">
    {{ post.content }}
    </div>
    <p class="preadmore"><a href="{{ BASE_PATH }}{{ post.url }}" alt="Read More" class="readmore"><span>&#10149;</span>Read More</a></p>
    </div>
  {% endfor %}
</div>



