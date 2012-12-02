---
layout: index
title: "Kingauthur's Blog"
description: "池逸欣(kingauthur)的博客首页，这里有关于互联网的分析，技术的讨论，生活的点点滴滴，旅行的意义"
keywords: "池逸欣，博客，kingauthur，技术贴，互联网，旅行的意义，生活"
---
{% include JB/setup %}




<div id="content">
    <article id="post_list">
      {% for post in site.posts %}
        <section class="post">
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
      {% endfor %}
    </article>
</div>

<script type="text/javascript">
  showCurrentItem(document.getElementById("menu-item-index"));
</script>



