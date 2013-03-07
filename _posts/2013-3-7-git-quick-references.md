---
layout: post
category : 工具
tags : [git github quickstart]
---

## git : [the simple guide](http://rogerdudler.github.com/git-guide/index.zh.html) 

### 基本命令

### 创建新仓库
	
	git init
	
### 克隆一个本地仓库

	git clone /path/to/repository 

如果是远端服务器上的仓库

	git clone username@host:/path/to/repository

### 添加计划改动

	git add <filename>
	git add *

###  实际提交

	git commit -m "代码提交信息"

###  推送到协作仓库

	git push origin master

	可以把 master 换成你想要推送的任何分支。 

### 本地仓库链接到某远程

	git remote add origin <server>

## 分支

是用来将特性开发绝缘开来的。在你创建仓库的时候，master 是“默认的”。在其他分支上进行开发，完成后再将它们合并到主分支上。
除非你将分支推送到远端仓库，不然该分支就是 不为他人所见的：

### 创建（比如feature_x)

	git checkout -b feature_x
### 切换回主分支：
	git checkout master
### 删除
	git branch -d feature_x

### 分支推送到远端仓库

	git push origin <branch>

### 更新远程仓库到本地仓库

	git pull


### 合并其他分支到当前分支（例如 master），执行：

	git merge <branch>

### 合并成功后通知git
	git add <filename>

### 在合并改动前，可查看差异
	git diff <source_branch> <target_branch>
###  标签：1.0.0 
	git tag 1.0.0 1b2e1d63ff

1b2e1d63ff 是你想要标记的提交 ID 的前 10 位字符。使用如下命令获取提交 ID：

### 查看Log

	git log
你也可以用该提交 ID 的少一些的前几位，只要它是唯一的。

### 替换工作目录改动 类似revert 
	git checkout -- <filename>


### 丢弃全部本地改动与提交
	git fetch origin
	git reset --hard origin/master

### 贴士

内建的图形化 git：
	gitk
彩色的 git 输出：
	git config color.ui true
显示历史记录时，只显示一行注释信息：
	git config format.pretty oneline
交互地添加文件至缓存区：
	git add -i
 