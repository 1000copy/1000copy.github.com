---
layout: page
---
{% include JB/setup %}

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

 [新浪微博](http:/t.cn) 
 内网[trdwiki](http://trdwebserver:8082/trdwiki)
 [q2a](http://192.168.12.247/q2a)
 <img src="http://www.gravatar.com/avatar/88caadc211781b5ba82d07e435443213">



