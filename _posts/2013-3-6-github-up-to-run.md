GitHub那么流行，不去玩玩，还是技术人员吗？
我们这次玩完后，你可以

	* 占坑。在github上有了自己的座位
	* 建坑。在本地建立版本库
	* 玩坑。提交代码到本地库
	* 同步。同步代码修改到远程库

然后，你就理解，如日中天的github是怎么回事了，下次别人提到github，你也就不焦虑了。

对啊。哥玩过了。

####占坑

看到new repository(创建项目仓库），就点击下。这就是创建代码仓库了。

在GitHub，一个项目对应唯一的Git版本库



接下来的很平常，给个项目的名字和描述。从产品，到婴孩，万万千千的新事物，谁不需要一个名字呢。
反正都是第一次玩，你肯定要删除的。因此不必你动脑筋，给他一个 “helloworld” 。省省心吧。不外乎就是小明，狗剩之类的。


再来就比较high了。然后，github会给我们一个command line提示，用这些命令行就可以把占坑，建坑，玩坑，同步，一路完成。


	mkdir helloworld
	cd helloworld
	git init
	git add README.md
	git commit -m "first commit"
	git remote add origin https://github.com/USERNAME/helloworld.git
	git push -u origin master

作为一个svn用户，我就傻了。svn多简单啊。

	svn checkout
	svn update
	svn commit 

就完了。那三板斧劈起来，虎虎生风。

不一样了。要保持清醒。我保准说，你用过svn的经验，不但不能有益，反而有害。就好像用过vss的人，现在玩svn了，也是一样的道理。

这都是些啥？我知道，英文我看得懂，可是放到一起，我就不太懂了。

怎么这个git这么啰嗦呢？


当然，模式不同了，设计就是这样。我们不懂，我们照做——把命令挨着敲了一边。

因为是第一次用，不是Existing Git Repo？就不必看后面了。

git config --global ...

这些事情，还是比较好懂，就是告诉git默认使用的用户账号和email，以后就必须每次输入用户名了。

#### 建坑

建立目录,以后代码都往这个目录放。懂啊。

	mkdir helloworld
	cd helloworld

然后，初始化本地代码仓库：

	git init
	git add README.md
	git commit -m "first commit"


作为和版本工具相关的第一个命令，git init， 就不太懂了。

对应svn第一步是checkout，服务器有代码仓库了，客户端只要checkout就行。

可是git不是这样。git是无中心的。git本地依然有仓库，要单独初始化。你的代码提交到本地，log写到本地，可以在本地开分支，可以在本地回溯，不依赖作为服务器的中心节点——一个正常版本管理功能，都可以在本地做。只有需要和其他人协调的时候，才会push到共享库上去。

同样是版本管理工具，git被称为分布式，而svn被称为集中式。根本差别！需要认真体会。

在接下来的git add README.md ;git commit ....。语义上来说，就是把文件加入，并且提交到版本库。你这个命令，即使不联网也可是成功运行的。提交到代码库（commit )提交到本地了。svn commit可是必须联网的。

#### 玩坑

这个命令，很妖艳。除了cisco ios之外，我还没有见过这么长的命令呢。

	git remote add origin http://github.com/USERNAME/helloword.git 


字面意思是 远程 添加 源 源URL。好，先把字面放到一边。我们停下来，撸一撸。

git是分布式的版本管理。就是说，我们工作时，可以同时又多个版本管理仓库并存。

现在就是这样——我们现在就已经有了2个版本仓库了。

	* github的，通过界面上提供的一系列操作建立起来。
	* 通过git init，在本地目录建立起来。

那么，本地库要同步到github库时，本地库必须知道github库的地址。bingo！ 这就是git remote add origin URL的含义——告诉本地版本库，当提交同步时，把它同步到指定URL标示的远程库上去。这里，就是 http://github.com/USERNAME/helloword.git


哦。为了解释清楚 git remote add origin 这个命令，用了好多长句子啊 。

最后一条命令。git push 执行推送命令，完成推送到 GitHub 版本库的。
	 
	$ git push -u origin master


* 可是还有 -u 呢。-u 参数，在推送成功后自动建立本地分支与远程版本库分支的追踪。
* 可是还有 origin master 呢。这个命令选项，是说，把分支master（默认分支）推送到远程版本库去。

天啊。可是，什么是分支呢。

这个分支，就不是本文的主题了。反正你按照这个方式先死记硬背吧。

我把他们都讲完了。


  
