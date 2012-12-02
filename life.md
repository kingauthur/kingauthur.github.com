---
layout: index
title: "池逸欣的生活志"
description: "池逸欣的生活志，用来记录和分享生活的点点滴滴，爱生活生命才精彩"
keywords: "池逸欣，生活志，生活点点滴滴"
---
{% include JB/setup %}

<div id="content">
    <article>
      {% for post in site.posts %}
         {% if post.category == 'life' %}
	        <section class="life">
		          <h2><a href="{{ BASE_PATH }}{{ post.url }}" class="title">{{ post.title }}</a></h2>
		          <small class="meta">{{ post.date | date: "%m - %d - %Y" }}</small>
		        <div class="content">
		         {{ post.description }}
        
		        {% if post.img != null %}
		            <img src="{{ post.img }}">
		        {% endif %}
		        </div>
		    	<!-- 标签 -->
		        <ul class="tag_box inline">
		      		{% assign tags_list = post.tags %}
		      		{% include JB/tags_list %}
		      	</ul>
		      	<br/>
		      	<!-- readmore按钮 -->
		        <p class="preadmore"><a href="{{ BASE_PATH }}{{ post.url }}" alt="Read More" class="readmore"><span>&#10149;</span>阅读全文</a></p>
        	</section>
	     {% endif %}
      {% endfor %}
    </article>
</div>

<script type="text/javascript">
	showCurrentItem(document.getElementById("menu-item-life"));
</script>