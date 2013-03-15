---
layout: post
category : 语言
tags : [鸡血]
---

关于 Dropwizard 的第一句话，就把老子震动了。Dropwizard straddles the line between being a library and a framework。凭着这一点，我想要继续看下去。先把它up and run 起来。

我认为它的卖点，就是把 http server ，servlet 内置了，一个fat-jar 全部搞定。

直观的就是，要启动一个web 程序，只要

java -jar xxx.jar mainclass 

就行了。你看不到  http server ，servlet。当然也需要安装tomcat，apache，配置他们，把自己的thin-jar丢进去。然后一百遍的做同样的重复工作了。

那么，第二个问题就接踵而至。你的那些自定义的http server，比起apache,tomcat怎么样？

于是，第二个牛逼就继续奔袭而来。 Its goal is to provide performant, reliable implementations of everything a production-ready web service needs 。
替代品也是有名字的。jetty for http ,jersey for REST ,jackson for json 。
牛逼一旦开始，就不能停了：）。
不管怎样，它有些符合我的审美情趣——就是一体化，简洁，干净。我有继续看的兴趣了。


0. 当然，下载dropwizard

我用github for windows做这个事情，就是一个clone即可。
下载下来的，构建采用的工具是maven，人家都是喜欢不用ide的人。
问题是，我喜欢ide！
我需要 eclipse 项目。还好，maven可以生成 eclipse 项目

于是——

1. 安装maven

解压下载包，然后

set JAVA_HOME=C:\jdk1.5.0_06
set PATH=%JAVA_HOME%\bin;%PATH% 

每种新技术都会有老根底，对吗

2. 生成eclipse工程

mvn eclipse:eclipse

这个命令会下载一堆依赖于%USER_HOME%\.m2\repository 内，并且在dropwizard目录内生产eclipse工程文件

3. trouble shooting

3.1 打开eclipse ,导入dropwizard所在目录

这时，会发现一堆堆的错误，像是这样：
     The project cannot be built until build path errors are resolved Unbound classpath variable: 'M2_REPO/
因为maven下载的依赖文件都在 M2_REPO 内，eclipse必须知道 M2_REPO 位于何处。因此这个问题解决的关键在于加入 M2_REPO class path 。

4. 告诉 eclipse ,M2_REPO 的值

这篇文章写得比较清楚，涉及到图片，我就不移动到本文内了。特别提示， M2_REPO 必须是大写
http://www.mkyong.com/maven/how-to-convert-maven-java-project-to-support-eclipse-ide/

3.2  rebuild 即可发现刚刚的问题消失。

这样，就完成了dropwizard 自我化的第一步。喊一句口号吧:

dropwizard ,forked .
