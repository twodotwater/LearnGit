Git is a distributed version control system.
Git is a free sofeware.

**
How to install Git on windows?

http://msysgit.github.io/	//windows版本的git

git config --global user.name "name"	//指定用户名和Email
git config --global user.email "**@**.com"

**
How to use Git?

git init //创建版本库
git add readme.txt //添加文件到仓库
git commit -m "描述信息" //提交修改、并且添加修改说明
git status	//仓库当前状态
git diff	//查看修改信息
git log	--pretty=oneline	//查看提交历史记录
git log --graph --pretty=oneline --abbrev-commit	//查看分支合并图
git reflog		//查看命令历史记录
git reset --hard HEAD^ //回退上一次版本。HEAD表示当前版本；HEAD^上一版本；HEAD^^上上一版本；HEAD~100上100个版本。
git reset --hard commitid	//回到指定版本号。Note：与log 、reflog协同使用！
git checkout -- file	//撤销修改。1、未添加暂存区，恢复和版本库状态一致；2、添加暂存区后修改，恢复和暂存区状态一致。
git reset HEAD file 	//添加暂存区后，撤销回工作区。
git rm file 	//删除文件。恢复：Reset ；确认：commit

**
How to use GitHub?

ssh-keygen -t rsa -C "email@**.com"		//生成ssh Key：rsa、rsa.pub
GitHub --> Settings --> Add SSH Key --> title / rsa.pub

Create a new repo --> repo name 	//在GitHub上创建一个仓库
git remote add origin https://github.com/twodotwater/repository.git		//关联GitHub仓库
git push -u origin master	//推送内容到GitHub仓库，且master分支和远程的master分支关联
git clone https://...git	//克隆GitHub仓库到本地

git checkout -b <name>	//创建并切换分支
git branch		//查看所有分支，当前分支前有*号
git branch <name>	//创建新的分支
git checkout <branch>	//切换到分支
git branch -d <name>	//删除分支，分支已合并
git branch -D <name>	//强制删除没有合并过的分支
git merge <dev>		//合并分支，将当前分支指向dev分支
git merge --no-ff -m "description" <dev>	//禁用fast forward来合并分支、添加描述信息

*
Bug branch 【Bug分支】

git stash	//保存当前工作现场<branch current-work>
>> git checkout <branch bug>	//切换到Bug出现的分支
git checkout -b <issue01>	//创建新的处理Bug的分支
>> git checkout <branch bug>	//切换到Bug出现的分支
git merge --no-ff -m "description" <issue01>	//合并处理了Bug的分支
git branch -d <issue01>		//删除处理Bug的分支，完成其任务
git checkout <branch current-work>	//返回到之前进行的工作分支
git stash list		//查看所有保存的现场
git stash pop	//恢复并清理保存的现场
git stash apply stash@{0}	//恢复某个现场状态
git stash drop	//清理保存的现场

*
Work together 【多人协作】

git remote		//查看远程仓库信息
git remote -v 	//显示详细仓库信息

git push origin <branch>	//推送某个分支到远程仓库。Tips：master/dev等重要分支与远程同步！

git clone <address> 	//克隆远程库。Note：默认情况下、只能看到master分支！
git checkout -b dev origin/dev		//创建远程origin的dev分支到本地
git branch --set-upstream dev origin/dev	//设定dev和origin/dev链接
git pull 	//抓取远程内容到本地。Note：如果本地合并冲突，先解决冲突，再提交push更新到远程库！

*
Tag 【标签】（某一时刻仓库的版本，即版本库的一个快照，指向某commit的指针）

git tag <name> 		//打一新标签。Note：默认打在最新提交的commit上
git tag <name> commitid		//为某次提交打标签
git tag -a <name> -m "description"		//打标签时添加说明信息
git tag -s <name> -m "description"		//用私钥签名一个标签。Note：采用PGP签名，需安装（GnuPGP）！
git tag		//查看所有标签。Note：字母排序！
git show <tagname>		//查看标签信息

git tag -d <tagname>	//本地删除一个标签
git push origin :refs/tags/<tagname>	//远程删除某个标签
git push origin <tagname>	//推送一个标签到远程库
git push origin --tags		//推送全部未推送的标签到远程库


