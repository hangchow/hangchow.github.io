---
layout: post
title: transfer request from nginx to tomcat 
---

{{ page.title }}
================

<p class="meta">31 May 2012 - Shanghai</p>
<p class="meta">centos5</p>

最简单的方法就是修改/etc/nginx/nginx.conf,增加

<code> 
  server {
    listen 80;
    server_name yourdomainname;
    location / {
         proxy_pass http://localhost:8080;
    }
  }
</code>

8080是本地tomcat启动端口.
