流程: 
ssh-keygen, 获取本地的密钥, 储存在本地路径下的id_rsa.pub文件 --> 建立本地与git仓库的联系
git init: 初始化本地仓库，生成.git隐藏文件
git config --list --> 本地配置信息列表
git remote add origin src --> 使本地仓库与git仓库中的指定src储存库建立联系, 命名为origin
git add --<file>  提交到暂存区
git commit -m 'msg' 提交到本地仓库
git reset --hard HEAD <file> 回退一个版本 --mixed: 回退到提交暂存区之前 --soft：回退到提交本地仓库之前
git pull/push origin master --> 拉/推到origin下的master分支

git remote rename a b --> 把a名称改为b

修改远程仓库： git remote set-url --push [name] [newUrl]
工作区恢复到上一个暂存状态： git checkout 
提交本地test分支作为远程的master分支: git push origin test:master
查看用户信息：$ git config --global user.name/user..email
设置用户信息：$ git config --global user.name/user.email "John Doe"/johndoe@example.com
git branch 查看本地所有分支
git status 查看当前状态
git remote show origin 显示远程库origin里的资源
git fetch 相当于是从远程获取最新版本到本地，不会自动merge
