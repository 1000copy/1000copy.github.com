---
layout: post
category : scala
tagline: "play scala up and run on Mac"
tags : [tutorial]
---

前置条件：
安装java 1.6以上
下载play，展开zip到一个可读可写的目录内

步骤：
1. add the framework installation directory to your system PATH

export PATH=$PATH:/relativePath/to/play

2.  make sure that the play script is executable 

	$ chmod a+x play

3. Check that the play command is available

	$ play help

4. create new app

	$ play new todolist

5. What is the application name? 
> todolist

6. Which template do you want to use for this new application? 

  1             - Create a simple Scala application
  2             - Create a simple Java application

> 1
OK, application todolist is created.

Have fun!

7. 看看现在有什么

app/ models, controllers and views where .scala source files live.
conf/ 配置文件，比如路由配置。
public/ JavaScript, stylesheets and images 
test/    Tests are written as Specs2 specifications.

8. up to run

$ cd todolist/
$ play
Getting org.scala-sbt sbt 0.12.2 ...
:: retrieving :: org.scala-sbt#boot-app
	confs: [default]
	40 artifacts copied, 0 already retrieved (8381kB/115ms)
[info] Loading project definition from /Users/lcjun/play/todolist/project


