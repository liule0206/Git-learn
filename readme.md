## GIT学习
### Git 初始化
```bush 
$ git init
```

### 查看git 状态
```bush 
$ git status 
```

### 查看修改
```bush 
$ git diff 
```

### 文件上传
```bush 
$ git add 文件名 
$ git commit -m '说明' 
```

### 查看提交记录
```bush 
$ git log 
```
- 参数 `--pretty=oneline` 在一行显示简略信息

### 回滚 
```bush 
$ git reset --hard
```
- 可以跟版本号 版本号一般取前几位就可以
- 可以跟`HEAD`, `HEAD`表示当前版本,`^`表示上一个版本,`^^`表示上两个版本, `HEAD~100`表示前一百个版本

### 查看命令记录
```bush 
$ git reflog
``` 

### 撤销修改
```bush
$ git checkout -- <file>
```
- 一种 readme.md修改后没有放到暂存区`git add` ,现在撤销就回到和版本库一模一样的状态。
- 一种 readme.md修改后已经放到暂存区，又做了修改，现在，撤销修改就回到添加到暂存区后的状态
- `--` 很重要，如果没有--就变成切换到另一个分支 

### 撤销暂存区修改
```bush 
$ git reset HEAD <file> 
```

### 删除文件 
+ 删除已提交文件 
```bush
$ - git rm <file>
```
+ 本地文件删除了，但是服务器上没有删除
```bush 
$ git checkout -- <file>
```
### 将本地文件添加到远程仓库
```bush
$ git remote add origin git@github.com:liule0206/Git-learn.git
```
+ liule0206 换成自己的用户名
+ 远程库的名字 Git-learn 

 ### 把本地文库内容全部推送到远程库上
+ 第一次提交
```bush 
$ git push  -u Git-learn master
```
+ 以后每次提交
```bush 
$ git push origin master
```

### 从远程仓库克隆
```bush 
$ git clone  git@github.com:liule0206/Git-learn.git
```

### 创建分支
```bush 
$ git checkout -b dev
```
+ `git checkout`命令加上`-b`参数表示创建并切换，相当于以下命令
```bush 
$ git branch dev
$ git checkout dev
```
### 查看分支
```bush 
$ git branch
```
+ `git branch` 命令会列出所有分支，当前分支前面会有一个`*`号

### 将`dev`分支合并到`master`
```bush
$ git checkout master #切换到`master`分支上
$ git merge dev 
```
+ `git merge`命令用于合并指定`(dev)`到当前分支。

### 删除分支
```bush 
$ git branch -d dev
```
+ `-d` 表示删除




