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
git reset --hard commitid	//回到指定版本号。NOTE：与log 、reflog协同使用！
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
git branch -d <name>	//删除分支
git merge <dev>		//合并分支，将当前分支指向dev分支
git merge --no-ff -m "description" <dev>	//禁用fast forward来合并分支、添加描述信息

*
Bug branch

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


