---
layout: post
category : 工具
tags : [jekyll github]
---
{% include JB/setup %}


前一段时间，传出了gfw因为github pages而封锁github的消息。根据@fenng的三定律，我觉得我必须学习下github pages 了。

#### 好处

都是Blog发布的货。但是和wordpress这样的Blog Engine相比，Pages的好处还是有的：

	* 内文本，外格式
	* 自带版本管理

#### 快速起步只要三分钟

我最终采用的方式是[jekyllbootstrap](http://jekyllbootstrap.com/)的建议，3分钟搞定。因为实在是简单，并且用了王牌的bootstrap 美化了界面——就是说，不费力就得到看得过去的UI。

看到Demo Page后，我把代码中英文 brand，catogories,tag 等修改成为中文，就可以发布博客了。

#### 绑定域名

github给每个用户提供的是类似USERNAME.github.com的域名。这不专业！

如果需要绑定自己的美好的域名，还是应该看看 [阮一峰](http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html) 的。可以顺便理解了git和jekyll的的基本使用。然后完成域名的绑定。

方法也是比较简单的：

1. 根目录下面，新建一个名为CNAME的文本文件，里面写入你要绑定的域名，如example.com
2. 如果是顶级域名，则DNS要新建一条A记录，指向204.232.175.78。
3. 如果是二级域名，则DNS要新建一条CNAME记录，指向USERNAME.github.com。
4. 此外，别忘了将_config.yml文件中的baseurl改成根目录"/"。不然，等待你的是404！

#### 这是未来

[TW 技术雷达](http://thoughtworks.fileburst.com/assets/technology-radar-october-2012.pdf) 声称 

	【Jekyll(Jekyll)代表了网站发布领域的框架的“微观化”。当关注点只有一个，博客网站尽可能透明，并且指向一个更轻量级的未来。一个我们喜欢的例子就是现在发布软件项目有用的文档更加轻松了】

句子很长。我也不明白，直到我尝试安装完前。然后，我发现这句话可以翻译成为人话。

	他就是说: Wordpress作为blog发布工具，功能太全太复杂，太依赖数据库，有很多业务逻辑——麻烦而且有安全漏洞。Jekyll就是对立面：不需要数据库，自带版本备份，简单透明。当然简单，连评论功能都没有。你得用第三方的。

鉴于技术雷达不太不靠谱，如果你相信他所说的网站发布的微观化未来，那么，还应该进一步看看 Jekyll创始人的示例库 ，以及其他用Jekyll搭建的blog 。

你忙吧。我是准备歇歇了。
 
