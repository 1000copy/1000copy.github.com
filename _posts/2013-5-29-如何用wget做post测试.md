
## 如何使用wget 做form post？

我以前拿wget就是下载，尽管用什么都可以下载，但是看着wget黑乎乎的屏显，就是洋溢着快乐。

其实wget也可以做form提交，比如登录某个网站后下载东西。还可以记录cookie，然后再次提交。

1. 如果一个Login是这样的

<HTML>
<HEAD>
<TITLE></TITLE>
<META http-equiv=Content-Type content="text/html; charset=UTF-8">
</HEAD>


<form method="post" action="http://m.hifiwiki.net/user/login/2">
    <input name="usrname" type="text" size="24" maxlength="60" value="1000copy"/>
    <input name="psw" type="password" size="10" maxlength="20" value="1"/>    
    <input name="user_login" class="butt" type="submit" value="进入"/>
</form>

2. 那么 对于的wget提交就是

   wget --post-data="usrname=1000copy&psw=1&user_login=进入" localhost

3. 可以在php 一侧验证这个提交是否有效  
  
编辑  index.php
  
  <?
	 echo "d:";
	 echo $_GET["usrname"];
	 echo $_POST["usrname"];
	 echo $_SERVER['HTTP_USER_AGENT'] ;
  ?>
启动php服务器
	\php\php -S  localhost:80

4. curl 应该也有效，只是我的curl好像不支持localhost 

  curl --form "usrname=1000copy&psw=1&user_login=进入" localhost/test.php 
