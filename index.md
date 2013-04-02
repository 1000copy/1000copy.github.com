---
layout: page
---
{% include JB/setup %}

	     2
brucebot   350 天前
分页的使用如下:
_config.xml里面加上 paginate: 5 //每一页显示的文章数

index.html里面加上:

<div id="pagination">
<div class="pagenavi">
<span class="page_number">第{{paginator.page}}页/共{{paginator.total_pages}}页</span>
<a href="/">第一页</a>
{% if paginator.previous_page %}
{% if paginator.previous_page == 1 %}
<a href="/" class="current"><<前一页</a>
{% else %}
<a href="/page{{paginator.previous_page}}"><<前一页</a>
{% endif %}
{% else %}
<span><<前一页</span>
{% endif %}
{% for count in (2..paginator.total_pages) limit:8 %}
{% if count == paginator.page %}
<span class="current-page">{{count}}</span>
{% else %}
<a href="/page{{count}}">{{count}}</a>
{% endif %}
{% endfor %}

{% if paginator.next_page %}
<a href="/page{{paginator.next_page}}">后一页>></a>
{% else %}
<span>后一页>></span>
{% endif %}
<a href="/page{{paginator.total_pages}}">最后一页</a>
</div>
</div>


<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

[捐赠#互助读书#，改善熟人互动](http://www.up2run.com/markdown/2013/03/10/%E4%BA%92%E5%8A%A9%E5%80%9F%E4%B9%A6%E8%AE%A1%E5%88%92/)

<div class="anypay-button" width="20" height="20"></div>
 

