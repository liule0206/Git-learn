# GIT学习
+ 摘录自 廖雪峰的官方网站<http://www.liaoxuefeng.com/>Git教程
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
>* 因为用了VScode，有冲突不允许保存，需要先解决冲突才可以。
>+ 查看分支合并图
>```bush
>$ git log --graph
>```

## 分支管理-分支管理策略
>### 分支合并参数
>+ 通常，合并分支时，如果可能，Git会用Fast forward模式，但这种模式下，删除分支后，会丢掉分支信息。如果要强制禁用Fast forward模式，Git就会在merge时生成一个新的commit，这样，从分支历史上就可以看出分支信息。
>```bush
>$ git merge --no-off -m "merge with no-ff" dev
>```
>+ `--no-ff`参数，表示禁用`Fast forward`；
>+ 

## 分支管理-贮藏（修复BUG）
>### 贮藏代码
>```bush
>$ git stash 
>```
>### 查看贮藏的代码
>```bush 
>$ git stash list 
>```
>### 取出贮藏的代码
>```bush
>$ git stash apply
>$ git stash drop
>```
>+ `apply`将代码恢复，`drop`删除`stash`中保存的记录
>+ 也可以通过如下命令直接恢复并删除
>```bush
>$ git stash pop
>```
>+ 可以多次`stash`,恢复的时候先用`git stash list`查看，然后恢复指定的stash，用命令
>```bush
>$ git stash apply stash@{0}
>```

## 分支管理-多人协作
>### 查看远程仓库信息
>```bush
>$ git remote
>```
>+ 可以通过`git remote -v`显示更多信息
>```bush
>$ git remote -v
>origin	git@github.com:liule0206/Git-learn.git (fetch)
>origin	git@github.com:liule0206/Git-learn.git (push)
>```
>+ 上面显示了可以抓取和推送的`origin`的地址，如果没有推送权限，就看不到`push`的地址
>### 推送分支
>+ 推送分支，就是把该分支上的所有本地提交推送到远程库。推送时，要指定本地分支，这样，Git就会把该分支推送到远程库对应的远程分支上：
>```bush
>$ git push origin master
>```
>+ 如果要推送其它分支。如`dev`分支
>```bush
>$ git push origin dev
>```
>+ 推送分支的说明
>   * `master`分支是主分支，因此要时刻与远程同步；
>   * `dev`分支是开发分支，团队所有成员都需要在上面工作，所以也需要与远程同步；
>   * `bug`分支只用于在本地修复bug，就没必要推到远程了，除非老板要看看你每周到底修复了几个bug；
>   * `feature`分支是否推到远程，取决于你是否和你的小伙伴合作在上面开发。
>### 关于多人协作的工作模式
>+ `多人协作时提交代码会遇到一些问题，暂时先不考虑`
>+ 多人协作的工作模式通常如下：
>   1. 首先，可以试图用git push origin branch-name推送自己的修改；
>   2. 如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；
>   3. 如果合并有冲突，则解决冲突，并在本地提交；
>   4. 没有冲突或者解决掉冲突后，再用git push origin branch-name推送就能成功！
> 如果`git pull`提示`“no tracking information”`，则说明本地分支和远程分支的链接关系没有创建，用命令`git branch --set-upstream branch-name origin/branch-name`。
>### 小结
>+ 查看远程库信息，使用`git remote -v`；
>+ 本地新建的分支如果不推送到远程，对其他人就是不可见的；
>+ 从本地推送分支，使用`git push origin branch-name`，如果推送失败，先用git pull抓取远程的新提交；
>+ 在本地创建和远程分支对应的分支，使用`git checkout -b branch-name origin/branch-name`，本地和远程分支的名称最好一致；
>+ 建立本地分支和远程分支的关联，使用`git branch --set-upstream branch-name origin/branch-name`；
>+ 从远程抓取分支，使用`git pull`，如果有冲突，要先处理冲突。

## 标签管理
>### 添加标签
>+ 可以通过`git tag <name>`添加新标签，
>+ 例如给dev分支添加标签v0.0.5,命令如下：
>```bush
>$ git branch  
>$ git checkout dev
>$ git tag v0.0.5
>```
>+ 可以用命令`git tag` 查看所有标签
>```bush
>$ git tag
>v0.0.5
>```
>+ 如果历史版本忘记打标签可以通过commit id添加标签
>```bush
>$ git log --pretty=online --abbrev-commit
>$ git tag v0.0.2 6222222
>```
>+ `6222222`是对应提交记录的id
>+ * 标签不是按照时间顺序排序，而是按照字母顺序排序的
>+ 可以用过`git show <tagname>`查看标签信息
>```bush
>$ git show v0.0.2
>```
>+ 可以创建带有说明的标签，用`-a` 指定标签名，用`-m`指定标签说明文字；
>```bush
>$ git tag -a v0.0.3 -m "version 0.0.2 branch" 278b662
>```
>+ 还可以通过`-s`用私钥签名一个标签：
>```bush
>$ git tag -s v0.0.5 -m "signed version 0.0.5 dev" 394dd44
>
>error: cannot run gpg: No such file or directory
>error: could not run gpg.
>error: unable to sign the tag
>```
>+ 签名采用PGP签名，因为没有安装gpg（GunPG），
>+ 同样使用`git show <tagname>`查看PGP签名信息
>### 小结
>* 命令`git tag <name>`用于新建一个标签，默认为`HEAD`，也可以指定一个commit id；
>* `git tag -a <tagname> -m "xinxixinxixinxi..."`可以指定标签信息；
>* `git tag -s <tagname> -m "xinxixinxixinxi..."`可以用PGP签名标签；
>* 命令`git tag`可以查看所有标签。
>###操作标签
>+ 如果标签打错了，也可以删除：
>```bushh
>$ git tag -d v0.0.0
>```
>+ 因为创建的标签都只存在本地，不会自动推送到远程，所以，打错的标签可以在本地安全删除。
>+ 如果要推送某个标签到远程，使用命令`git push origin <tagname>`;
>```bush
>$ git push origin v0.0.1
>```
>+ 或者，一次性推送全部尚未推送到远程的本地标签：
>```bush
>$ git push origin  --tags
>```
>+ 如果标签已经推送到远程，要删除需要先删除本地标签，然后，从远程删除，删除命令也是`push`,命令如下：
>```bush
>$ git tag -d v0.0.1
>$ git push origin :refs/tags/v0.0.1
>```
>### 小结
>* 命令`git push origin <tagname>`可以推送一个本地标签；
>* 命令`git push origin --tags`可以推送全部未推送过的本地标签；
>* 命令`git tag -d <tagname>`可以上删除一个本地标签；
>* 命令`git push origin :refs/tags/<tagname>`可以删除一个远程标签。

##自定义Git
>+ 让Git显示颜色，会让命令输出看起来更醒目：
>```bush
>git config --global color.ui true
>```
>### 配置别名
>+ 如`git status`想要简写成`git st`
>```bush
>$ git config --global alias.st status
>$ git config --global alias.ci commit
>$ git config --global alias.br branch
>```
>+ 以后提交就可以写成：
>```bush
>$ git ci -m "bala bala balb..."
>```
>+ `--global`参数是全局参数，也就是这些命令在这台电脑的所有Git仓库下都有用。
>+ 命令`git reset HEAD file`可以把暂存区的修改撤销掉(unstage),重新放回工作区。既然是一个unstage操作，就可以配置一个`unstage`别名：
>```bush
>$ git config --global alias.unstage 'reset HEAD'
>```
>+ 当你敲如命令
>```bush 
>$ git unstage readme.md
>```
>+ 实际上Git执行的是：
>```bush
>$ git reset HEAD readme.md
>```
>+ 这样用`git last`，让其显示最后一次提交信息：
>```bush
>$ git config --global alias.last 'log -1'
>```
>+ 来点狠的`lg`
>```bush
>$ git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
>```
>+ 有木有感觉很方便，很方便！好激动的说。
>### 配置文件
>+ 配置Git的时候，加上`--global`是针对当前用户起作用的，如果不加，那只针对当前的仓库起作用。
>+ 每个仓库的Git配置文件都放在了`.git/config`文件夹中。
>+ 别名就在`[alias]`后面，要删除别名，删除对应行就可以。配置别名也可以直接修改这个文件。

##其他



