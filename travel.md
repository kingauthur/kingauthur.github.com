---
layout: index
title: "Kingauthur's 走走停停"
description: "池逸欣的走走停停，用来记录和分享旅行途中的一切，包括看到的，听到的，遇到的，想到的"
keywords: "池逸欣，走走停停，旅行"
---
{% include JB/setup %}

<div id="content">
    <article idd="post_list">
      {% for post in site.categories.travel %}
	        <section class="post">
		          <h2><a href="{{ BASE_PATH }}{{ post.url }}" class="title">{{ post.title }}</a></h2>
		          <small class="meta">{{ post.date | date: "%m - %d - %Y" }}</small>
		        <div class="content">
		        	 {{ post.content | truncatehtml: 269 }}
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
      {% endfor %}
    </article>
</div>

<!--分页器-->
<div id="pagination">
  第1页/共1页 前一页 1 后一页
</div>


<script type="text/javascript">
	showCurrentItem(document.getElementById("menu-item-travel"));
</script>