---
title: GIT
date: 2018-12-10 15:24:14
tags: git
---
## 认识 Git
分布式版本控制系统（Distributed Version Control System，简称 DVCS）面世了。 Git 就是一个典型的分布式版本控制系统。

这类系统，客户端并不只提取最新版本的文件快照，而是把代码仓库完整地镜像下来。 这么一来，任何一处协同工作用的服务器发生故障，事后都可以用任何一个镜像出来的本地仓库恢复。 因为每一次的克隆操作，实际上都是一次对代码仓库的完整备份。下图来源于Git官网。
### Git 的三种状态
Git 有三种状态，你的文件可能处于其中之一：

•已提交（committed）：数据已经安全的保存在本地数据库中。
•已修改（modified）：已修改表示修改了文件，但还没保存到数据库中。
•已暂存（staged）：表示对一个已修改文件的当前版本做了标记，使之包含在下次提交的快照中。

由此引入 Git 项目的三个工作区域的概念：Git 仓库(.git directoty) 、工作目录(Working Directory) 以及 暂存区域(Staging Area) 。

基本的 Git 工作流程如下：
•在工作目录中修改文件。
•暂存文件，将文件的快照放入暂存区域。
•提交更新，找到暂存区域的文件，将快照永久性存储到 Git 仓库目录。

## Git 使用快速入门
### 获取Git
* 在现有的目录中初始化仓库：进入项目目录运行 `git init` 命令,该命令将创建一个名为 .git 的子目录。
* 从一个服务器克隆一个现有的Git仓库：`git clone [url] directoryname`（directoryname为本地仓库即文件夹的名称，可选）。

### 记录每次更新到仓库
* 检测当前文件状态：`git status` 。
* 提出更改（把它们添加到暂存区）：`git add *`(所有文件)、`git add filename` (针对特定文件)、`git add *.txt`（支持通配符，所有 .txt 文件）。
* 忽略文件：.gitignore 文件(可在里面配置不需要提交的文件)。
* 提交更新：`git commit -m "代码提交日志"`（每次准备提交前，先用 `git status` 看下，是不是都已暂存起来了， 然后再运行提交命令 git commit）。
* 跳过使用暂存区域更新的方式 : `git commit -a -m "代码提交信息"`。git commit 加上 -a 选项，Git 就会自动把所有已经跟踪过的文件暂存起来一并提交，从而跳过 git add 步骤。
* 移除文件 ：`git rm filename` （从暂存区域移除，然后提交。）
* 对文件重命名 ：`git mv README.md README`(这个命令相当于`mv README.md README`、`git rm README.md`、`git add README` 这三条命令的集合)。

### 推送改动到远程仓库
* 如果你还没有克隆现有仓库，并欲将你的仓库连接到某个远程服务器，你可以使用如下命令添加：
  	`git init` #git初始化
	`git remote add origin https://github.com/用户名/你的GitHub用户名.github.io.git` #添加仓库地址
	`git checkout -b 分支名` #新建分支并切换到新建的分支
	`git add .` #添加所有本地文件到git
	`git commit -m "这里填写你本次提交的备注，内容随意"` #git提交
	`git push origin 分支名` #文件推送到hexo分支
### 查看提交历史
在提交了若干更新，又或者克隆了某个项目之后，你也许想回顾下提交历史。 完成这个任务最简单而又有效的工具是 `git log` 命令。git log 会按提交时间列出所有的更新，最近的更新排在最上面。
只看某个人的提交记录：`git log --author=zhaozg`

### 分支
分支是用来将特性开发绝缘开来的。在你创建仓库的时候，master 是“默认的”分支。在其他分支上进行开发，完成后再将它们合并到主分支上。
我们通常在开发新功能、修复一个紧急 bug 等等时候会选择创建分支。单分支开发好还是多分支开发好，还是要看具体场景来说。
创建一个名字叫做 test 的分支：`git branch test`
切换到test分支：`git checkout test`
创建分支 test 并切换（上面两个的合并）：`git checkout -b test`
合并分支到当前分支上：`git merge test`
将 test 分支推送到远端仓库（推送成功后其他人可见）：`git push origin test`

[参考链接:](https://mp.weixin.qq.com/s/ylyHOuEPX4tDvOc7-SxMmw)
