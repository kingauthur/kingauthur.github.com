---
layout: post
title: "Hello jekyll"
description: "本文介绍基于jekyll+markdown+git+github快速搭建blog的入门方法，以及自己对此的一些认识和相关资料的官方文档。
<br/>
<br/>
在学习git的时候，偶然间接触到了[jekyll],继而逐渐深入了解后，发现，git+[github]+jekyll+[markdown]，这不就是我想要的写博客工具么，轻量、简洁、便捷，故当即决定用这个套装搭建新的Blog。以前的文章决定不再迁过来了，反正也很久没写了，重头再来过。  
"
category: tech
tags: [jekyll,blog]
---
{% include JB/setup %}

在学习git的时候，偶然间接触到了[jekyll][1],继而逐渐深入了解后，发现，git+[github][2]+jekyll+[markdown][3]，这不就是我想要的写博客工具么，轻量、简洁、便捷，故当即决定用这个套装搭建新的Blog。以前的文章决定不再迁过来了，反正也很久没写了，重头再来过。  

言归正传，这几天初识了下git+[github][2]+jekyll+[markdown][3]这个套装，个人比较喜欢这么几点：
1. 轻，真的很轻。每个页面都是静态的`html`，所以根本就不需要应用服务器，web服务器就搞定了，当然，数据库也省了。
2. 方便。直接托管在github上，再绑定下域名的指向，如果你买VPS只为搭blog的话，那这笔小费也可以省了。顺便，因为git的关系，还能做到离线写文章。
3. 清晰，写文章清晰。当然，这是和markdown有关，markdown易写的语法以及完全使用自己本地文本编译器的方式，让在blog系统上写文章重新变回了一种享受。
4. 方便折腾。对于喜欢自己布局或者正在学习布局的同学们来说，能在本地折腾而且不需要重新deploy，这个很诱人。

---------  

因为自己电脑的关系，下面介绍下mac下jekyll的安装步骤，其他OS的参考下[官方安装文档][4]吧

1. 用RubyGems安装Jekyll:

		$ gem install jekyll
	如果执行的时候遇到  `Failed to build gem native extension` 错误，说明是本地的ruby版本不够新，需要1.9.3的版本，官方文档说碰到这个情况，使用
			
		$ sudo gem update --system
	但是一般都是会提示已经更新到最新，反正我是不行，如果你碰到和我一样的情况，那就直接安装一个ruby-1.9.3好了.推荐用选择[RVM][5]安装，关于RVM的说明，可以参考下官网的说明。安装完RVM后，直接执行:
		
		$ rvm install 1.9.3
	如果一切顺利的话，就安装完了，你再执行安装jekyll的命令就。但本人人品不好，安装过程中，出现了  

	>ERROR: Error running \' ./configure  
	>--prefix=/Users/dionnesaunders/.rvm/rubies/ruby-1.9.3-p0  
	>--enable-shared --disable-install-doc  
	>--with-libyaml   
	>--with-opt-dir=/Users/dionnesaunders/.rvm/usr \',  
	>please read /Users/dionnesaunders/.rvm/log/ruby-1.9.3-p0/configure.log

	打开`configure.log`文件后，说是`C compiler cannot create executables`，在网上搜了下，应该目前xcode下带的gcc版本和安装ruby所需的gcc版本不一致，所以就自己去网上找了单独的mac下的gcc，叫[*osx-gcc-installer*][6]，
	可以自行去下载。下载完安装后就可以安装jekyll了。  

2. 安装Jekyll-Bootstrap：  
有些人可能会问，这个又是什么东西？捎带下概念，Jekyll不是一个blog系统，只是一个模版解析引擎，说的简单点，就是将*.md*,*.textfile*这些文本格式解析成*.html*格式的解析器，而Jekyll-Bootstrap是一套使用Jekyll的快速建站工具。
具体的可以看下[Jekyll Introduction][7]。言归正传，安装命令如下：
	 
		$ git clone https://github.com/plusjade/jekyll-bootstrap.git  your's filename
	当然，前提你需要一个github的账号，如果你没有，可以参考[Github Dashboard][8]。
	你也直接将blog托管在github上，这需要你在github创建一个版本，用*USERNAME*.github.com命名，then:
		
		$ git clone https://github.com/plusjade/jekyll-bootstrap.git USERNAME.github.com
		$ cd USERNAME.github.com
		$ git remote set-url origin git@github.com:USERNAME/USERNAME.github.com.git
		$ git push origin master

	然后进入到刚才的根目录，执行：

		$ jekyll --server
	你就可以通过<http://localhost:4000>本地访问了，想发布到github上去，就执行：
	
		$ git add .
		$ git commit -m "Add new content"
		$ git push origin master
	这样就可以通过*USERNAME*.github.com访问了。

3. 其他相关的资料。  
*   如果你选择托管在github上，但是想绑定自己的域名，那么请参考[GitHub Pages][9]。
*   如果你想部署到自己的VPS,也很方便，可以参考[Deployment][10]。
*   如果你想参考其他利用jekyll搭建的网站，可以参考[Site List][11]。
*   如果你想了解下markdown，可以参考下[markdown语法说明][12]。
*   如果你想在mac下找一款除了VIM其他的支持markdown语法的文本编辑器，你可以试试[Mou][13]。
*   如果你想把以前的blog迁移过来，可以参考[blog migrations][15]。
*   更多的关于jekyll的使用和介绍，可以参考[start blogging][14]。
		

[1]: http://jekyllrb.com/ "jekyll官网"
[2]: https://github.com/ "github官网"
[3]: http://daringfireball.net/projects/markdown/ "markdown参考"
[4]: https://github.com/mojombo/jekyll/wiki/Install "jekyll官网安装文档"
[5]: https://rvm.io/ "rvm官网"
[6]: https://github.com/kennethreitz/osx-gcc-installer/downloads
[7]: http://jekyllbootstrap.com/lessons/jekyll-introduction.html "Jekyll的官网说明"
[8]: https://github.com/ "Github官网"
[9]: http://help.github.com/pages/ "jekyll,如何绑定自己的域名"
[10]: https://github.com/mojombo/jekyll/wiki/Deployment "jekyll,自定义部署"
[11]: https://github.com/mojombo/jekyll/wiki/Sites "jekyll,实例网站"
[12]: http://markdown.tw/#philosophy "markdown语法说明"
[13]: http://mouapp.com/ 
[14]: http://jekyllbootstrap.com/usage/index.html "jekyll入门介绍"
[15]: https://github.com/mojombo/jekyll/wiki/Blog-Migrations "关于blog的迁移"
