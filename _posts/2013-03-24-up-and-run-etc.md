---
layout: post
category : blog
tags : [新闻]
---

鉴于这段时间做技术雷达研究，会有种种的up and run。因此，干脆把所有的简单up and run 都集中发到这里。

#### php up and run on mac 10.8 

php 和apache已经内置于mac 10.8 之内，需要的只是打开开关。

1. Edit /private/etc/apache2/httpd.conf
shortcut by command + shift + G ,go the dir directly 
2. Find the line that says LoadModule php5_module libexec/apache2/libphp5.so and uncomment it by editing out the # at the beginning of the line. (Then save the file, obviously.)
3. Go to Terminal and type sudo apachectl graceful at the console
4. Go to chrome ,type localhost/
5. You will view a poge : It works 
6. change root ,DocumentRoot to new location

7. troubleshooting 

在浏览器中运行出现在You don't have permission to access / on this server.  提示。查了一下apache手册找到问题所在处。这里定义了默认对网站根的访问权限。
# Each directory to which Apache has access can be configured with respect
# to which services and features are allowed and/or disabled in that
# directory (and its subdirectories). 
#
# First, we configure the "default" to be a very restrictive set of 
# features.  
#
<Directory />
    Options FollowSymLinks
    AllowOverride None
    Order deny,allow
    Deny from all 
</Directory>
这里改成
<Directory />
    Options Indexes FollowSymLinks
    AllowOverride None
</Directory>
问题解决
8. php work .new a.php file ,then visit localhost/a.php

<?php
phpinfo();
?>

7. setup Mysql

下载一个DMG，150M多，要等一会儿。完毕后，打开dmg，看到一个mysql.pkg 这个是mysql的安装包，点击就可以安装mysql，还有一个mysql.prefPane,点击它就可以按照一个配置面板，有了它，就可以在mac的偏好设置内看到mysql项目，在这里可以start /stop mysql。第三个是关于自启动的，我对它没有兴趣，就不管了。

	how I find mysql command line is ?
	$find / -name mysql 
	  result : /usr/local/mysql-5.6.10-osx10.7-x86_64/bin/mysql
	  export PATH=$PATH:/usr/local/mysql-5.6.10-osx10.7-x86_64/bin
8. popu data

	create database bb;
	use bb;
	drop table  if exists book;
	create table book(
		 id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
	     title NVARCHAR(100) NOT NULL,
	     douban_id int ,
	     author_id int,
	     devote_id int
	);

	insert into book (title)values("当我们跑步时，我们谈些什么");
	insert into book (title)values("悉尼");
	insert into book (title)values("联想风云");


how do I find out if my air is 64 or 32bit?


It's 64-bit. All of the MacBook Air versions use Core 2 Duo processors, which are 64-bit processors. The kernel won't be running in 64-bit mode (as @Mathew's answer showed you how to find out), but that in no way limits you to 32-bit apps. OS X can run each program in a different mode, and tries to run each program in the best possible mode -- many programs come with both 32- and 64-bit code included, and the OS will automatically pick the best one for your CPU. If you run the Activity Monitor utility, it'll show you what programs are currently running (including invisible background programs), and its "Kind" column will show what mode they're running in -- I'll bet more than half are "Intel (64 bit)".



