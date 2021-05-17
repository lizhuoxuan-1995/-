流程: 
ssh-keygen, 获取本地的密钥, 储存在本地路径下的id_rsa.pub文件 --> 建立本地与git仓库的联系
git init: 初始化本地仓库，生成.git隐藏文件
git config --list --> 本地配置信息列表
git remote add origin src --> 使本地仓库与git仓库中的指定src储存库建立联系, 命名为origin
git pull/push origin master --> 拉/推到origin下的master分支

git remote rename a b --> 把a名称改为b

修改远程仓库： git remote set-url --push [name] [newUrl]
工作区恢复到上一个暂存状态： git checkout 
提交本地test分支作为远程的master分支: git push origin test:master
查看用户信息：$ git config --global user.name/user..email
设置用户信息：$ git config --global user.name/user.email "John Doe"/johndoe@example.com
git branch 查看本地所有分支
git remote show origin 显示远程库origin里的资源
git fetch 相当于是从远程获取最新版本到本地，不会自动merge


git log --pretty=oneline: 查看提交历史
git reflog --pretty=oneline: 查看命令历史记录


## 基础
$ git remote add origin git@git.zhlh6.cn:lizhuoxuan-1995/conflict.git: 关联一个远程库
关联一个远程库时必须给远程库指定一个名字，origin是默认习惯命名

$ git push -u origin master: 加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。

$ git remote -v: 查看远程库信息
$ git remote rm origin: 解除本地和远程的绑定关系


## 改
$ git checkout -- readme.txt: 丢弃工作区的修改, 有两种情况：
一种是readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和**本地版本库**一模一样的状态；
一种是readme.txt已经 git add 到暂存区后，又做了修改，现在，撤销修改就回到**添加到暂存区后**的状态。
总之，就是让这个文件回到最近一次git commit或git add时的状态。

$ git reset HEAD readme.txt 把暂存区的修改撤销掉（unstage），重新放回工作区

$ git rm readme.txt 从版本库中删除该文件, 并且git commit
tips: 手动删除文件后，使用git rm <file>和git add<file>效果是一样的。


## 分支
$ git checkout -b dev: 创建dev分支，并切换到dev分支， 等同于：$ git branch dev，$ git checkout dev
$ git branch： 查看当前分支，git branch命令会列出所有分支，**当前分支**前面会标一个*号。

$ git merge dev： 合并**指定分支(dev)**到**当前分支**

git branch -d dev: 删除dev分支