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
</script>
 <!-- 在需要的地方加入按钮 —->
<div class="anypay-button"></div>

<!-- 在合适的地方链入AnyPay脚本 -->
<script type="text/javascript" src="http://guoyu-app.b0.upaiyun.com/pay.js"></script>
<!-- 配置按钮参数 -->
<script type="text/javascript">
	var payInfo = {
		// 需要开通收款主页
		baseUrl: 'https://me.alipay.com/guoyu', 
		payAmount: 10,
		payReason: '捐赠anyPay插件，为了更好的社区支付'
	}
	anyPay.init(payInfo);
</script>
<script src="http://s85.cnzz.com/stat.php?id=5081690&web_id=5081690" language="JavaScript"></script>
<a href="http://rizhibao.com" name="rizhi5cd393699b5748eefa4361bde95f8827bao" >日志宝</a>
