---
layout: post
title: github和jekyll写博客 
tags: jekyll github disqus blog
---

{{ page.title }}
================

<p class="meta">31 May 2012 - Shanghai</p>

今天想写点东西,狗狗到几篇比较好的文章:

 * [Publishing a Blog with GitHub Pages and Jekyll](http://blog.envylabs.com/2009/08/publishing-a-blog-with-github-pages-and-jekyll/)
 * [Getting Started With Jekyll](http://asymmetrical-view.com/2009/05/14/starting-wtih-jekyll.html)

----------------------------------

失败过n次后, 总结成功步骤:

* 安装rvm

参考[使用rvm在Mac中安装ruby和rails](http://blog.prosight.me/index.php/2011/09/805).

* rvm安装ruby

<pre>
rvm install 1.9.2
</pre>

* 安装rubygems

 参考[ruby-rails-leopard](http://hivelogic.com/articles/ruby-rails-leopard/).

* gem改成淘宝的镜像

<pre>
sudo gem sources --remove http://rubygems.org/ 
sudo gem sources -a http://ruby.taobao.org/ 
</pre>

* 安装jekyll

<pre>
gem install jekyll rdiscount
</pre>

* 搞模版

直接用github老大的[tom.preston-werner](https://github.com/mojombo/mojombo.github.com).

* 写博客

我用[markdown](http://daringfireball.net/projects/markdown/syntax), 貌似github扩展了更多的md语法.
另外要学习模版的用法[jekyll wiki](https://github.com/mojombo/jekyll/wiki/).

* 本地博客

启动jekyll:
<pre>
jekyll  --auto --server 
</pre>
访问[http://localhost:4000](http://localhost:4000), 可边修改边看效果.

* 安装disqus

把下面的js搞到jekyll post模版里:
[Universal Code](http://docs.disqus.com/developers/universal/)
打开disqus的开发模式方便本地博客:
<pre>
var disqus_developer = 1;
</pre>

* 设置rss

下次再搞

* 上传到github

你能看到本文,说明上传到github已经生效了!
