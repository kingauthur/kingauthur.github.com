---
layout: index
title: "Kingauthur's 技术贴"
description: "池逸欣的技术贴，用来记录和分享遇到的新鲜好玩的技术，或者互联网产品，或者工作上遇到的技术难题"
keywords: "池逸欣，技术贴，互联网"
---
{% include JB/setup %}

<div id="content">
    <article id="post_list">
      {% for post in site.categories.tech %}
	        <section class="post">
		          <h2><a href="{{ BASE_PATH }}{{ post.url }}" class="title">{{ post.title }}</a></h2>
		          <small class="meta">{{ post.date | date: "%m - %d - %Y" }}</small>
		        <div class="content">
					{{ post.content | split:'<!--break-->' | first }}	        
    			</div>
		    	<!-- 标签 -->
		        <ul class="tag_box inline">
		      		{% assign tags_list = post.tags %}
		      		{% include JB/tags_list %}
		      	</ul>
		      	</br>
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
	showCurrentItem(document.getElementById("menu-item-tech"));
</script>