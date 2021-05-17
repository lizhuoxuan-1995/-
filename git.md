
修改远程仓库： git remote set-url --push [name] [newUrl]
提交本地test分支作为远程的master分支: git push origin test:master
git remote show origin 显示远程库origin里的资源
git fetch 相当于是从远程获取最新版本到本地，不会自动merge


## 基础

ssh-keygen: 获取本地的密钥, 储存在本地路径下的id_rsa.pub文件 --> 建立本地与git仓库的联系
git init: 初始化本地仓库，生成.git隐藏文件
git remote add origin src: 使本地仓库与git仓库中的指定src储存库建立联系, 命名为origin

git config --list: 本地配置信息列表

git remote rename a b: 把a名称改为b

git log --pretty=oneline: 查看提交历史
git reflog --pretty=oneline: 查看命令历史记录

$ git remote add origin git@git.zhlh6.cn:lizhuoxuan-1995/conflict.git: 关联一个远程库
关联一个远程库时必须给远程库指定一个名字，origin是默认习惯命名

$ git push -u origin master: 加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。

$ git remote -v: 查看远程库信息
$ git remote rm origin: 解除本地和远程的绑定关系

$ git config --global user.name/user.email: 查看用户信息
$ git config --global user.name/user.email "John Doe"/johndoe@example.com: 设置用户信息


## 版本回退
$ git checkout -- readme.txt: 丢弃工作区的修改, 有两种情况：
一种是readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和**本地版本库**一模一样的状态；
一种是readme.txt已经 git add 到暂存区后，又做了修改，现在，撤销修改就回到**添加到暂存区后**的状态。
总之，就是让这个文件回到最近一次git commit或git add时的状态。

$ git reset HEAD readme.txt 把暂存区的修改撤销掉（unstage），重新放回工作区

$ git rm readme.txt 从版本库中删除该文件, 并且git commit
tips: 手动删除文件后，使用git rm <file>和git add<file>效果是一样的。

** 分步回退一个版本
$ git reset --soft HEAD：撤销commit
$ git reset HEAD file： 撤销add
$ git checkout -- file： 撤销工作区


## 分支
$ git switch -c dev: 创建dev分支，并切换到dev分支， 等同于：$ git branch dev，$ git switch dev

$ git branch： 查看当前分支，git branch命令会列出所有分支，**当前分支**前面会标一个*号。

$ git merge dev： 合并**指定分支(dev)**到**当前分支**

$ git branch -d dev: 删除dev分支

$ cherry-pick 4c805e2: 复制一个特定的提交到当前分支, Git自动给dev分支做了一次提交，注意这次提交的commit是1d4b803，它并不同于master的4c805e2，因为这两个commit只是改动相同，但确实是两个不同的commit。用git cherry-pick，我们就不需要在dev分支上手动再把修bug的过程重复一遍。


## 临时隐藏文件

$ git stash 

$ git stash list: 查看

$ git stash pop: 恢复的同时删除stash内容, 等同于: $ git stash apply: 恢复 + git stash drop: 删除

$ git stash apply stash@{index}: 多次stash时，恢复到指定版本  越早stash的版本index越大


## 配置别名

$ git config --global alias.st status: status --> st

**本地配置对照
co --> checkout
ci --> commit
br --> branch
li --> log --pretty=oneline