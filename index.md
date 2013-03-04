---
layout: page
title: Hello World!
tagline: Supporting tagline
---
{% include JB/setup %}

一个超链接 [新浪微博](http:/t.cn)

## 标题

代码 :
    
    title : My Blog =)
    
    author :
      name : Name Lastname
      email : blah@email.test
      github : username
      twitter : username

最新博客:

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

 [powered by jekyll-bootstrap](http://github.com/plusjade/jekyll-bootstrap)!



