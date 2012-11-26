---
layout: index
title: Less is more，simple is elegance
tagline: Supporting tagline
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



