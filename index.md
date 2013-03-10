---
layout: page
---
{% include JB/setup %}

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

 [新浪微博](http://t.cn/1000copy) 


<script type="text/javascript" src="http://guoyu-app.b0.upaiyun.com/pay.js"></script>
<!-- 配置按钮参数 -->
<script type="text/javascript">
	var payInfo = {
		// 需要开通收款主页
		baseUrl: 'https://me.alipay.com/1000copy', 
		payAmount: 10,
		payReason: '捐赠#互助读书#，改善熟人互动'
	}
	anyPay.init(payInfo);
</script>
<div class="anypay-button"></div>
<script src="http://s85.cnzz.com/stat.php?id=5081690&web_id=5081690" language="JavaScript"></script>
<a href="http://rizhibao.com" name="rizhi5cd393699b5748eefa4361bde95f8827bao" >日志宝</a>
