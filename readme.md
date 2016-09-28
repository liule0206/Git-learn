# GIT学习
## 基本
> ### Git 初始化
>```bush 
>$ git init
>```
>### 查看git 状态
>```bush 
>$ git status 
>```
> ### 查看修改
>```bush 
>$ git diff 
>```
## 版本操作
>### 文件上传
>```bush 
>$ git add 文件名 
>$ git commit -m '说明' 
>```
>### 查看提交记录
>```bush 
>$ git log 
>```
>- 参数 `--pretty=oneline` 在一行显示简略信息
>### 回滚 
>+ 回退到上个版本
>```bush 
>$ git reset --hard HEAD^
>```
>- 可以跟版本号 版本号一般取前几位就可以
>- 可以跟`HEAD`, `HEAD`表示当前版本,`^`表示上一个版本,`^^`表示上两个版本, `HEAD~100`表示前一百个版本
>### 查看命令记录
>```bush 
>$ git reflog
>``` 
>### 撤销修改
>```bush
>$ git checkout -- <file>
>```
>- 一种 readme.md修改后没有放到暂存区`git add` ,现在撤销就回到和版本库一模一样的状态。
>- 一种 readme.md修改后已经放到暂存区，又做了修改，现在，撤销修改就回到添加到暂存区后的状态
>- `--` 很重要，如果没有--就变成切换到另一个分支 
>### 撤销暂存区修改
>```bush 
>$ git reset HEAD <file> 
>```
>### 删除文件 
>+ 删除已提交文件 
>```bush
>$ git rm <file>
>```
>+ 本地文件删除了，但是服务器上没有删除
>```bush 
>$ git checkout -- <file>
>```
## 远程仓库
>### 将本地文件添加到远程仓库
>```bush
>$ git remote add origin git@github.com:liule0206/Git-learn.git
>```
>+ liule0206 换成自己的用户名
>+ Git-learn 远程库的名字
>### 把本地文库内容全部推送到远程库上
>+ 第一次提交
>```bush 
>$ git push -u Git-learn master
>```
> 添加后，远程库的名字就是`origin`，这是Git默认的叫法，也可以改成别的，但是`origin`这个名字一看就知道是远程库。
>+ 以后每次提交
>```bush 
>$ git push origin master
>```
> ### 从远程仓库克隆
>```bush 
>$ git clone  git@github.com:liule0206/Git-learn.git
>```
>- 当你第一次使用Git的clone或者push命令连接GitHub时，会得到一个警告：
>```bush
>The authenticity of host 'github.com (xx.xx.xx.xx)' can't be established.
>RSA key fingerprint is xx.xx.xx.xx.xx.
>Are you sure you want to continue connecting (yes/no)?
>```
>- 这是因为Git使用SSH连接，而SSH连接在第一次验证GitHub服务器的Key时，需要你确认GitHub的Key的指纹信息是否真的来自GitHub的服务器，输入yes回车即可。
>### 小结
>* 要关联一个远程库，使用命令`git remote add origin git@server-name:path/repo-name.git`；
>* 关联后，使用命令`git push -u origin master`第一次推送master分支的所有内容；
>* 此后，每次本地提交后，只要有必要，就可以使用命令`git push origin master`推送最新修改；
>* 从远程仓库克隆`$ git clone git@server-name:path/repo-name.git`

## 分支管理-创建与合并
>### 创建分支
>```bush 
>$ git checkout -b dev
>```
>+ `git checkout`命令加上`-b`参数表示创建并切换，相当于以下命令
>```bush 
>$ git branch dev
>$ git checkout dev
>```
>### 查看分支
>```bush 
>$ git branch
>```
>+ `git branch` 命令会列出所有分支，当前分支前面会有一个`*`号
>### 合并分支
>+ 将`dev`分支合并到`master`
>```bush
>$ git checkout master //切换到`master`分支上 <name>
>$ git merge dev 
>```
>+ `git merge`命令用于合并指定`(dev)`到当前分支。
>### 删除分支
>```bush 
>$ git branch -d dev
>```
>+ `-d` 表示删除
>### 小结
>* Git鼓励大量使用分支：
>* 查看分支：`git branch`
>* 创建分支：`git branch <name>`
>* 切换分支：`git checkout <name>`
>* 创建+切换分支：`git checkout -b <name>`
>* 合并某分支到当前分支：`git merge <name>`
>* 删除分支：`git branch -d <name>`

## 分支管理-解决冲突
>### 




