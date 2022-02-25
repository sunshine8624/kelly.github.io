---
title: Git
---
***\*代码管理 ——\** Git基础**

![图片](https://mmbiz.qpic.cn/mmbiz_png/OtuoacnwftQiayAzfTeoOKz9MRLLsEBicOYxnviakXcOVk8DJhdLic4xPWrBq0Gj43GWQahwyoQg0jhsLT3FgZo6Fg/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

Git工作原理



1、**Workspace:工作区**，执行git add *命令就把改动提交到了暂存区，执行git pull命令将远程仓库的数据拉到当前分支并合并，执行git checkout [branch-name]切换分支。

2、**Index:暂存区**，执行git commit -m '说明' 命令就把改动提交到了仓库区（当前分支）。

3、**Repository:仓库区**（或本地仓库），执行git push origin master提交到远程仓库，执行git clone 地址将克隆远程仓库到本地。

4、**Remote:远程仓库**，就是类似github，coding等网站所提供的仓库。



Git显著优点就是**版本的分支（branch）和合并（merge）**十分方便。

github主要提供基于git的版本托管服务

git下载：https://git-scm.com/downloads/



![图片](https://mmbiz.qpic.cn/mmbiz_jpg/MXzNlnO3ib9Pxeun9OEYicdJiclWq5Tn0dD4YSLR3ic3bPoSuIUfoksbYibxWuC2VB7VuDNtkicpk5ibnrYnQ6oT6rooA/640?wx_fmt=jpeg&wxfrom=5&wx_lazy=1&wx_co=1)

**代码管理 —— Git与svn区别

**

**git分布式版本控制**

优点：1) 本地提交，在本地可以提交，创建分支，代码回滚。2) 每台开发机都是完整的仓库，便于恢复。

缺点：1) 缺乏对文件的权限控制。2) 学习相对复杂。

git commit 不需要网络，git push需要联网

![图片](https://mmbiz.qpic.cn/mmbiz_png/OtuoacnwftSMkf8nTw9mcCS8svYeJWcMlpVqliaNtz2VrFTX3kWI8vWnN2ATjunWn0O1HEMkjS8vllNHQo5wn0Q/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

「~git流程图~」



**svn集中式版本控制**

优点：1) 权限精细管理。2) 统一管理，概念简单

缺点：1) 中央服务器宕机机，则无法提交代码。2) 中央服务器故障会引起无法提交乃至历史记录全部丢失。

集中式版本控制系统最大的毛病就是必须联网才能工作

![图片](https://mmbiz.qpic.cn/mmbiz_png/OtuoacnwftSMkf8nTw9mcCS8svYeJWcMR8kU9VibgVoibM8G4OSwowKmsz5xAqO0lVqQIGicLU7l1QpSvJA5LgFibQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

「~svn流程图~」

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/MXzNlnO3ib9Pxeun9OEYicdJiclWq5Tn0dD4YSLR3ic3bPoSuIUfoksbYibxWuC2VB7VuDNtkicpk5ibnrYnQ6oT6rooA/640?wx_fmt=jpeg&wxfrom=5&wx_lazy=1&wx_co=1)

**代码管理 —— 常用git命令

**

新建代码库

\# 在当前目录新建一个Git代码库 

$ git init 

\# 新建一个目录，将其初始化为Git代码库 

$ git init [project-name] 

\# 下载一个项目和它的整个代码历史 

$ git clone [url]



配置

\# 设置提交代码时的用户信息

$ git config --global user.name "yourname"  // 设置用户名

$ git config --global user.email myemail@qq.com // 设置用户邮箱

\# 编辑Git配置文件 

$ git config -e [--global]

\# 显示当前的Git配置

$ git config --list  // 查看git设置列表信息



本地分支修改操作：

1、git checkout .    #本地所有修改回到原来的状态

2、$ git checkout -- app/index.html  #本地个别修改恢复。



命令行窗口没有关掉时（时光穿梭）

git log 查看历史

git reflog  查看命令历史，以便确定要回到未来的哪个版本。

恢复上一个版本  （ git reflog ）

git reset --hard 3628164



保存改动

git  stash   删除并保存改动

git  stash pop   恢复代码



修正提交最后一个 commit 消息

git commit --amend 或 git commit --amend -m "Fixes bug #42"



提交master后，如何处理

git push -f 命令去强制提交 （强行推送到远端）（不建议使用）

注：如果已经提交master分支，建议本地分支进行修改，重新提交。



删除远程分支

git fetch -p  本地删除远程已经删除的分支显示

git branch -a  用来查看远程分支

git push origin :feature/construction   删除远程分支



改下远程仓库push地址

git remote -v 查看现有远程仓库的地址url

\1. 修改命令

git remote set-url origin <URL> 更换远程仓库地址。把<URL>更换为新的url地址。

2､添加命令

git remote add jt https://github.com/TheChalice/OCManagerUI/invitation



删除node_modules文件夹

rm -rf node_modules/



wq保存并退出

（ shift+:） esc定位当前位置



Git仓库完整迁移 （注：新的git地址，需要建个分支）

\1. 随便找个文件夹，从原地址克隆一份裸版本库

git clone --bare 旧的git地址

\2. 推送裸版本库到新的地址

cd xxx.git git push --mirror 新的git地址



Git鼓励大量使用分支

查看分支：git branch

创建分支：git branch <name>

切换分支：git checkout <name>

创建+切换分支：git checkout -b <name>

合并某分支到当前分支：git merge <name>

删除分支：git branch -d <name>



取消一个目录的git初始化

执行rm -rf .git



查看详细的commit信息

git show 2e21737



### git rebase和git merge 

rebase 的概念/作用其实很简单——就是「变基」。具体来说，就是改变一条分支的「基点」，使原分支从指定的地方（commit）重新长出来。rebase 可以保证commit为一条线。

![图片](https://mmbiz.qpic.cn/mmbiz/OtuoacnwftSMkf8nTw9mcCS8svYeJWcMeAeKoKibuaTOwK89iabbxQavwHn5axFadmcoq62W08WtG8PRUpwuVEyg/640?wx_fmt=other&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz/OtuoacnwftSMkf8nTw9mcCS8svYeJWcMyLoSfTBjeTskqXVs5wsjyHqmOfl5kbsAd0C0EmENQyvP3cLKGeQ95g/640?wx_fmt=other&wxfrom=5&wx_lazy=1&wx_co=1)

注：git log --graph 提交记录的顺序问题

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/MXzNlnO3ib9Pxeun9OEYicdJiclWq5Tn0dD4YSLR3ic3bPoSuIUfoksbYibxWuC2VB7VuDNtkicpk5ibnrYnQ6oT6rooA/640?wx_fmt=jpeg&wxfrom=5&wx_lazy=1&wx_co=1)

***\*代码管理 ——\** 开发上线流程

**

![图片](https://mmbiz.qpic.cn/mmbiz_png/OtuoacnwftQiayAzfTeoOKz9MRLLsEBicOo9d4N2pyAYqQDz5CK4ED77JHrX1Hp4FvZHFoCRRCQXzewjxqancqXg/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/MXzNlnO3ib9Pxeun9OEYicdJiclWq5Tn0dD4YSLR3ic3bPoSuIUfoksbYibxWuC2VB7VuDNtkicpk5ibnrYnQ6oT6rooA/640?wx_fmt=jpeg&wxfrom=5&wx_lazy=1&wx_co=1)

**代码管理 —— 遇到的坑

**1、建议在代码提交之前先git merge develop 与develop进行同步。（减少冲突）

2、如果merge不成功，说明你的代码与别人的代码冲突了。需要怎么搞呢？

   1）首先git status 查看本地代码修改情况。

   2）通过以下命令，删除与恢复代码。

​        git stash  删除并保存改动

​        git  stash pop   恢复改动

​    注：用这个操作，一般都处理 merge不成功的问题。

3、git push -f 命令去强制提交 （强行推送到远端）（不建议使用）

4、**git fetch 和git pull 的差别**

\1) git fetch 相当于是从远程获取最新到本地，不会自动merge

\2) git pull：相当于是从远程获取最新版本并merge到本地

注：git pull是git fetch和git merge两个步骤的结合。

5、git 报错  gitThere is no tracking information for the current branch.

是因为本地分支和远程分支没有建立联系

git branch --set-upstream-to=origin/远程分支的名字 本地分支的名字

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/MXzNlnO3ib9Pxeun9OEYicdJiclWq5Tn0dD4YSLR3ic3bPoSuIUfoksbYibxWuC2VB7VuDNtkicpk5ibnrYnQ6oT6rooA/640?wx_fmt=jpeg&wxfrom=5&wx_lazy=1&wx_co=1)

**代码管理 —— 忽略特定的文件**

**
**

可以配置Git忽略特定的文件或者是文件夹。这些配置都放在.gitignore文件中。

下面我们看看常用的规则：

1）node_modules/  过滤整个文件夹

2）*.zip           过滤所有.zip文件

3）/mtk/do.c      过滤某个具体文件

