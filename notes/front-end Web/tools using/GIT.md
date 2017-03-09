## 创建版本库

可以在任何目录下创建。mkdir创建  cd进入目录  pwd 显示当前目录

git init 把当前目录变成git可管理的仓库

git status   可以查看本地仓库（工作区）的情况

git diff files  可以查看文件最后一次修改的地方

git add files  把工作区的修改提交到暂存区（如果报错找不到文件就手动创建一个文件或者确认文件是否在版本库内）

git commit -m 一次性提交暂存区的所有文件，-m后跟的是本次修改的说明。每次修改一定要先add后commit不然修改无法提交

git reset -- hard HEAD^/版本id     HEAD表示当前版本，上个版本就是HEAD^，也可直接写版本id（不用写全，写前几位也可）。

git log  查看修改提交历史，可以查看版本id。

git relog 查看命令历史，可以查看版本id（git bash窗口关后适用）

git checkout -- files 用暂存区覆盖工作区,可以丢弃工作区的修改

git reset HEAD files 用分支覆盖暂存区,可以丢弃暂存区的修改


## 创建SSH Key

ssh-keygen -t rsa -C "自己的邮箱"  在用户主目录里找到。用来给github识别是否是你自己提交的   可以用在多台电脑，提交不同的SSH key就可以。

git remote add origin
 https://github.com/vincytang/webdlearn.git  关联远程库

git push -u origin master   第一次推送
本地master的所有内容，以后可以简化，不写-u（-u是用来关联本地和远程的master分支）

git push origin master  把本地master分支的最新推送到远程仓库


## 克隆仓库

git clone GitHub给的仓库地址


## 分支   方便自己和对方能够同时工作且最后可以把成果合并到一起

git branch  查看分支

git branch name（分支名）  创建分支

git checkout name（分支名）  切换分支

git checkout -b name（分支名）  创建并切换分支

git merge name（分支名）   合并某个分支到当前分支

git branch -d name（分支名）   删除分支


查看本地仓库时出现以下提示怎么办？

Your branch is ahead of 'origin/master' by 4 commits.


因为本地超前于远程，所以要同步commit。执行git push命令。反之，执行git pull命令。


输入git log后不输入任何参数的命令后出现<END>怎么办？

按q退出


在合并分支时可能会使用fast-forward模式，这种模式在合并分支的时候分支的历史就已经被删除，看不出合并过。所以在大项目开发的时候最好不用ff模式。

禁用ff模式：

git merge --no-ff -m "merge with no-ff" name(分支名)

查看分支历史：

git log --graph --pretty=oneline

 --abbrev-commit

## bug分支

git stash  备份当前工作现场

git stash apply   恢复工作现场但不删除备份

git stash pop  恢复工作现场并删除备份

git stash list   查看stash

git stash apply stash@{0}(备份的版本id)   如果有多次stash的话可以选择恢复哪个版本


git branch -D name(分支名)     强制删除还没合并的分支
