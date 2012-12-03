---
layout: post
title: "为Jekyll添加静态搜索"
description: "之前讲过了如何用Jekyll搭建自己的Blog，不过作为一个静态的Blog系统，相比WordPress那些成熟的Blog系统，功能还薄弱了点，更别提其他花里胡哨的插件了。在这里，最缺的我觉得应该就是搜索功能了，没有搜索，就想没有了门，一个好的搜索，设置连目录都可以不要。  
</br>
</br>
在网上找了好久好久，翻了很多，大多都是利用plugin+js的方式，总感觉不是很喜欢。<a href='http://www.google.com/cse/manage/all'>Google Custom Search</a> 提供了另外一种方式，这个操作起来很简单，搜索功能也很强大，不过总给人感觉太重了，而且对于不稳定的网络，你懂的。  
</br>
</br>
于是找来找去，发现用<a href='http://jquery.com'>JQuery</a>搜索静态文本的API来解决，是最简单，也是最轻量级的方式。"
category: tech
keywords: "jekyll,blog,博客,搜索，search"
tags: [jekyll, blog]
---
{% include JB/setup %}

之前讲过了如何用Jekyll搭建自己的Blog，不过作为一个静态的Blog系统，相比WordPress那些成熟的Blog系统，功能还薄弱了点，更别提其他花里胡哨的插件了。在这里，最缺的我觉得应该就是搜索功能了，没有搜索，就想没有了门，一个好的搜索，设置连目录都可以不要。  

在网上找了好久好久，翻了很多，大多都是利用plugin+js的方式，总感觉不是很喜欢。[Google Custom Search](http://www.google.com/cse/manage/all) 提供了另外一种方式，这个操作起来很简单，搜索功能也很强大，不过总给人感觉太重了，而且对于不稳定的网络，你懂的。  

于是找来找去，发现用[JQuery](http://jquery.com)搜索静态文本的API来解决，是最简单，也是最轻量级的方式。下面我来说下方法：  


####一. 首先，需要准备工具，下几个[JQuery](http://jquery.com)文件，包括： 
  
* [jquery.js](http://code.jquery.com/jquery.js)
* [jquery-ui.js](http://code.jquery.com/ui/1.8.18/jquery-ui.js)
* [jquery-ui.css](http://code.jquery.com/ui/1.8.18/themes/base/jquery-ui.css)  
  
这三个文件用来动态搜索静态文本，以及提供默认的样式。  

####二. 现在有了工具，下面就需要准备源材料了。  
源材料很简单，就是准备一个文本文件，里面包含了Blog里面所有文章的内容。在根目录下新建一个**`search.xml`**，其实文件名无所谓，这样取名以后方便管理。文件的内容如下：  
	
	---
	layout: none
	---
	<?xml version="1.0" encoding="UTF-8" ?>
	<articles>
		{\% for post in site.posts %\}
		<article>
    		<title>{\{ post.title }\}</title>
    		<url>{\{ site.url }\}{\{ post.url }\}</url>
    		<date>{\{ post.date | date_to_utc | date: '%Y-%m-%d'}\}</date>
		</article>
		{\% endfor %\}
	</articles>
		
这个文件用来保存Blog里所有文章的**标题、日期以及文章的链接地址**。反斜杠是我转义用的，复制的时候记得去掉。  
	
####三. 现在源材料和工具都有了，到了如何把两者结合到一起了。
首先在你的页面上增加一个文本框：

	<input type="text"  id="search" size="30" placeholder="Search" required />  
		
你没看错，只需要一个文本框，甚至都不需要一个表单。

然后增加一段JS代码，内容如下：  
  
 	$(function() {
          $.ajax({
              url: "/search.xml",
              dataType: "xml",
              success: function( xmlResponse ) {
                 var data = $( "article", xmlResponse ).map(function() {
                      return {
                          value: $( "title", this ).text() + ", " +
                              ( $.trim( $( "date", this ).text() ) ),
                          desc: $("description", this).text(),
                          url: $("url", this).text()
                      };
                  }).get();
  
                  $( "#j_search" ).autocomplete({
                      source: data,
                      minLength: 0,
                      select: function( event, ui ) {
                        window.location.href = ui.item.url;
                      }
                  });
              }
          });
      });
        
	这段代码应该比较浅显易懂的，就是指定去解析**`search.xml`**，并且是通过`AJAX`异步交互的过程。文本框的`ID`要和JS文件里对应。    

####四. 最后一个可能不是步骤的步骤.
就是`AJAX`它是根据什么路径去查找相应的被解析的文本文件呢，所以需要你在**`_config.yml`**增加一段：

		url: 你Blog的域名。
		
好了，这样就大功告成了。不过这是一个非常简单的搜索功能，不能支持全文搜索，只支持对**标题**和**日期**的搜索，不过对我来说已经满足需求了。效果如下：

![demo](/assets/custom/photos/20121203/demo.png)



