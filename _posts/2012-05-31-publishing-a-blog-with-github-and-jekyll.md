---
layout: post
title: 托管于github的博客网站 
tags: jekyll github disqus blog
---

{{ page.title }}

------
版本更新:
<p class="meta">31 May, 2012 - Shanghai</p>
<p class="meta">20 Aug, 2021 - Home, Hangzhou</p>

--------

## 安装

* 安装ruby
    <pre>
    brew install ruby
    </pre>
    现在版本是3.0.2

* 设置墙内ruby镜像库

    改成华为版
    <pre>
    gem sources --add https://repo.huaweicloud.com/repository/rubygems/ --remove https://rubygems.org/
    </pre>

* 安装jekyll
    <pre>
    sudo gem install jekyll rdiscount -V
    </pre>
    等待漫长的过程。

* 选择模版

    [tom.preston-werner](https://github.com/mojombo/mojombo.github.com)

* 写博客

    我用[markdown](http://daringfireball.net/projects/markdown/syntax), 貌似github扩展了更多的md语法.
另外要学习模版的用法[jekyll wiki](https://github.com/mojombo/jekyll/wiki/).

* 本地效果

    启动jekyll:
    <pre>
    jekyll  --auto --server 
    </pre>
    访问[http://localhost:4000](http://localhost:4000), 可边修改边看效果.

* 可选：安装disqus

    把下面的js搞到jekyll post模版里:
[Universal Code](http://docs.disqus.com/developers/universal/)
打开disqus的开发模式方便本地博客:
    <pre>
    var disqus_developer = 1;
    </pre>

* 可选：设置rss

    待续


* 上传到github

    你能看到本文,说明上传到github已经生效了!


## 参考文献
* [Websites for you and your projects](https://pages.github.com/)
* [Getting Started With Jekyll](http://asymmetrical-view.com/2009/05/14/starting-wtih-jekyll.html)


