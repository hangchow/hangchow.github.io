---
layout: post
title: nginx代理tomcat 
categories: tools
tags: nginx centos tomcat
---

{{ page.title }}
================

<p class="meta">31 May 2012 - Shanghai</p>

最简单的方法就是修改/etc/nginx/nginx.conf,增加
<pre> 
  server {
    listen 80;
    server_name yourdomainname;
    location / {
         proxy_pass http://localhost:8080;
    }
  }
</pre>

8080是本地tomcat启动端口.
