---
layout: post
category : java
tags : [dropwizard java]
---
{% include JB/setup %}


#### 把 dropwizard-example 跑起来

没有耐性的，看看步骤

<pre>
1. 设置run conf 的主类为　com.example.helloworld.HelloWorldService

2. 装入数据
    java -jar target/dropwizard-example-0.3.0-SNAPSHOT.jar db migrate example.yml

3. 执行服务
    java -jar target/dropwizard-example-0.3.0-SNAPSHOT.jar server example.yml

4. 浏览器测试 
    输入 http://localhost:8080/hello-world
    看到 {"id":1,"content":"Hello, Stranger!"}
    就说明，它工作了

5. 不仅仅是URL映射，dropwizard还提供了管理接口
    http://localhost:8081/
</pre>
___________________________________________________
觉得还不过瘾？continue .

难道说，一个example，而且还是现成代码的project ，也需要教程吗？
官方的 getting started 从头到尾的讲解这个案例，并且不是基于eclipse来讲的。而我的这个教程，针对的是eclipse+现成的源代码来的。有点不同。就是说，我的才是真的getting started —— 不需要你一行行的敲入代码（或者拷贝粘贴），拿到案例，更快开始。

前文已经把dropwizard 无错的装入eclipse。这次我们要把 第一个工程 dropwizard-example 运行起来。

1. 运行  dropwizard-example的参数

在eclipse 直接执行  dropwizard-example 的 com.example.helloworld.HelloWorldService 主类，可以看到它给出提示

usage: java -jar project.jar [-h] [-v] {server,render,db} ...
positional arguments:
  {server,render,db}     available commands

提示信息是在讲，可以提供 server ,render ,db参数 ，那么具体server 等参数是什么意思呢。 readme.MD 的最后几句话指明了方向：

	* To setup the h2 database run.	
	        java -jar target/dropwizard-example-0.3.0-SNAPSHOT.jar db migrate example.yml
	
	* To run the server run.	
	        java -jar target/dropwizard-example-0.3.0-SNAPSHOT.jar server example.yml

就是说，运行ex这个项目，首先得把h2数据库跑起来，方法就是一命令行。当然，这个命令行在eclipse内也可以，把尾部的

db migrate example.yml

拷贝到run configaration -> arguments 内就行了。

2. Run with arguments

这次就比较顺利。也看到console内启动了一个webserver，并且有一些用法上的说明，比如访问端口号，比如可以用的url

3. It worked

访问URL： localhost:8080/hello-world
发现一个json data出现在浏览器内。

这就是说，它工作了。


4. 更多可以测试用的URL
    GET     /hello-world (com.example.helloworld.resources.HelloWorldResource)
    POST    /hello-world (com.example.helloworld.resources.HelloWorldResource)
    GET     /views/iso88591.ftl (com.example.helloworld.resources.ViewResource)
    GET     /views/iso88591.mustache (com.example.helloworld.resources.ViewResource)
    GET     /views/utf8.ftl (com.example.helloworld.resources.ViewResource)
    GET     /views/utf8.mustache (com.example.helloworld.resources.ViewResource)
    GET     /protected (com.example.helloworld.resources.ProtectedResource)
    GET     /people (com.example.helloworld.resources.PeopleResource)
    POST    /people (com.example.helloworld.resources.PeopleResource)
    GET     /people/{personId} (com.example.helloworld.resources.PersonResource)
