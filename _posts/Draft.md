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


##如何安静卸载软件

想我这样的常常玩软件的人，当厌倦了一个软件要卸载，反反复复的看到 “你要不要卸载”，以及跟着引导界面走，一次又一次，真的很蛋疼。

是否可以安静点？喊你走，你就走！

关键看软件是否支持安静卸载。而这和制作软件安装包的工具也有关系。

1.  Nullsoft Install System，虽然没有help选项，但是，可以用/S 选项做静默卸载。

比如foxmail就是用的 Nullsoft Install System，虽然并不提示可以安静卸载，但是假如/S就可以。只是，必须是大写S！
It is documented to work for the uninstaller also but it has to be uppercase (/S) and if you are calling the uninstaller from your installer to uninstall a older version you should also provide the special _?= uninstaller parameter. How silent it is depends on your code; a MessageBox without /SD will not be silent etc.

2. 如果是innosetup : 选项为 /verysilent 
比如：安静卸载rubyinstall ， "C:\rb\unins000.exe" /verysilent 
help ref：http://www.jrsoftware.org/ishelp/index.php?topic=setupcmdline

3. MSI的安装包，加入/qn就可以。那是相当的安静。举例子：

silverlight : MsiExec.exe /X{89F4137D-6C26-4A84-BDB8-2E5A4BB71E00} /qn
silverlight SDK 4:MsiExec.exe /X{2927F380-C7B2-415F-9057-E100532117AF} /qn
silverlight SDK 3:MsiExec.exe /X{18F8306B-E31B-4E52-8BD0-17A82EC0AFC4} /qn
4. ClickOnce Dotnet的发布制作工具的卸载

看到uninstall string 的字样为 rundll32.exe dfshim.dll，就可以知道这是clickonce 的安装程序。
比如： github就是采用ClickOnce打包的。Uninstall string 是这样的；

rundll32.exe dfshim.dll,ShArpMaintain GitHub.application, Culture=neutral, PublicKeyToken=317444273a93ac29, processorArchitecture=x86

对于这个类型的软件，是否可以Slient ？答案是NO。

You can not suppress the uninstall dialog for a ClickOnce application. You can write a small .net app to uninstall the ClickOnce application and programmatically hit the button on the dialog so not action is required by the user. That's about the best you can do.

或者借助另一个工具： https://github.com/6wunderkinder/Wunder.ClickOnceUninstaller


5. 未知制作工具

也可以试试/q 。比如 visual studio 这样的大型工具，静默卸载更有价值	

	"c:\Program Files (x86)\Microsoft Visual Studio 10.0\Microsoft Visual Studio 2010 Ultimate - CHS\setup.exe" /q

wmic 也可以静默卸载，只是，太慢了。伤心。

Don't over complicate it & keep it simple - this works on both Windows XP & 7:

Go to Add/Remove Programs and make note of the exact name of the program. Open Notepad and paste the text below:

wmic product where name="PROGRAM NAME" uninstall

but make sure to type the exact name of the program in between the quotation marks and chose Save As /All Files and name the file Uninstall.bat and then test it out to make sure it works.

## 技术管理五讲

定规矩
    规矩的价值
    规矩的博弈
	    从：我喜欢，我不喜欢。
	    到：我们喜欢，我们不喜欢		
	提高标准
		不可以本公司为标准
		反感不准时		
			准时很累
				少量需要准时
				要求必须做到
			不准时很轻松
				大部分不需要准时
				异步通知
		主动提供信息
			人
				人是第一位
				团队形象
				手下能干，自己当然能干
				05年重点推荐杨勇，09年李奕飞，10年马时飞，12梁桥 薛峰
				寻找卖点
				创造卖点
				获取资源
			想法和成果，随时email
			重视会议，做好准备，提供信息，给予反馈
			给予反馈
				考勤制度变换的启示：给领导反馈
				创造环境为了谁：给手下反馈
		技术雷达
	创造变化
		有定期数据源
		有目标，要行动，抢资源
		常有变化
			人性决定：人心思变，哪怕朝三暮四到朝三暮四

		变化种类
			组织，编程，工具，技术
	异步沟通
		email 
		曹刚遇到的沟通问题
		好处
			适合随时表达
			从容，不必立刻回复
			技术化，可以更好的描述技术问题
				dba的汇报希望
		使用
			微软沟通
			考勤审批
			需求审批
			问题,事件，成果
		垃圾邮件的处理
		QQ呢？
找目标

玩出花样：如何技能成长
	结对编程
		概念
		我和ljb
		张强+江峰
			快速学习习惯
			习惯触动高效
			编码之外
		张强+李浩
		杨千栋的看法
		如何选人？
		效果
			10年合作，50小时结对？
			同舟共济，并肩作战最难忘
			浪费一人？	
	Scrum
		基本过程
			每日站会
			任务分解
			贴纸飞飞
			画燃尽图
			每月冲刺
		软件 vs 纸飞飞
		我们
			薛峰水污染
			新打印
			ROS
			微博+gscrum+gmantis
		好处
			关注点集中
			每日压力
			快乐成就
	codejam + hackton+ 非常48
		概念
		我的担心
		发奖环节
		发现人才
		有趣：注意，人心思变
	双显示屏
	数据挖掘
		考勤的主题显示：考勤制度变换对加班时间的影响

掌控信息：提供与反馈
	投名状
	反馈给手下的必要性
	梁桥的调动引发的影响
	我欢迎的信息
	我如何主动提供的信息
	我觉得反馈很难
利用资源
	卢春的利用资源，平行的
	宋大成的，上行的
	我们的资源
	如何获取数据
		HR的人员
		行政部的车位
让会议有趣
	会议的价值
		强迫沟通
			人类的节奏
			知道大家在哪里
		强迫准备
			定时间，逼着自己弄想法			
			不怕讲的搓。3选1			
	会议形式：我们每天看到的
	我的反对
		长条桌，星形沟通，走流程
	我的实践 
	openday 
		形式，内容，周期,适用范围
	cafeday	
		形式，内容，周期,适用范围
	one to one 
		形式，内容，周期,适用范围
	standup 
		形式，内容，周期,适用范围

## 炮轰后的杂活/想法。

一次会议，被几个同事炮轰：你们的那个产品，太烂了。

具体是什么产品，其实关系不大，所以也就不提了。

我也承认不好用，因为我常常听说。可是，我也是有意见的。

1. 每次提到难用，都没有具体的难用点
2. 提不出具体的意见，是因为，他们不过是转述某人的意见
3. 之所以看不到正主的意见，是因为中间层次太多。用户，代理，客户服务，产品组，我们部门
4. 这样的,...咳咳咳...，的体系，持续多年。产品进步大才是怪事。

解决这个问题的关键，是杀掉全部中间环节，直接面对客户。我曾经这样想过，也试过。当然，这个解决方案的最大问题，是比要解决的问题本身还不可能。

那你还说个屁啊。有些人已经觉得无聊透骨，准备拂袖而去了。

我，还有一个想法。。。也不是什么新思路。就是，让用户通过我们的一个网络系统，和我们直接联络。

1. 模块可以直接升级
2. 可以直接提出需求和Bug
3. 所有的release，都公开到一个网站上

我们的产品不少，做一个网站绰绰有余。并且把开发者和最终用户一视同仁。

想想也害怕。模式变化很大，我们能够直接面对客户，直接运维和发布我们的产品。需要一个支撑体系，全新建立。

这样行吗？

需求：

面对公司客户，开发者，外部开发者，提供产品发布，自动更新，依赖检查。还有，自我更新。
1. 提供网上商店
2. 更新，依赖检查
2.1 断点续传
3. 模板更新、配置更新、数据更新、数据同步
4. 依赖下载比如msde
5. IIS配置

都是杂活！

使用场景

1. 安装vs
2. 各种推荐软件
3. 公司内的小产品，如小闹钟
4. 

该重视下网络了

从上周三而来，一直网络非常缓慢，trd 抱怨无法做事。
今天给邝总发一份邮件，发了15分钟，还是不行，最后想起，用我的3G网络发才成。

300年前，亚当斯密认为：修路可以促进经济发展，因为同样的产品可以销往更大的市场。

而信息的交换带来的创新价值不输于物流的开拓。

从上次抱怨公司 Email 以来，公司对这个事情，我感觉，其实还是不重视的。
其中关键我想：

一是未必理解低质量的网络上如何导致程序员工作效率急剧下降

二是缺乏配套的机制，以便保持网络的稳定和快速恢复。网络调整是否应该通知相关部门？对网络质量有看法，是否应该有表达的渠道？是否监控到恢复的时间和改进的进程？

我认为首要在于保证解决好创新的机制问题，减少这样的不必要的、导致“整个”开发过程低效的障碍。

自己的运维都做不好，自己的员工都不能从网络服务收益，还做什么产品的运维，让客户收益呢。



峰哥：

系统部要更换网站服务器，而我们在上面有两项古老的服务在运行。

建议停掉两项服务。

我调查过负责辉煌在线的项目经理，这个产品2年未发出，但是有人用，很少。
管家婆精华版也n年没有音讯，好像是针对深圳的一个客户做了一批。

1. 辉煌在线的授权管理网站。目前使用这个服务的产品只有“辉煌在线”，
2. 软狗授权的管理网站








