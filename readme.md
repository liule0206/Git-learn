## GIT学习
	# Git 初始化
		+ git init 
	# 查看git 状态
 		+ git status
	# 查看修改
		+ git diff 
	# 文件上传
		+ git add 文件名
		+ git commit -m '说明'
	# 查看提交记录
		+ git log 
		- 参数 --pretty=oneline 在一行显示简略信息
	# 回滚 
		+ git reset --hard 
			- 可以跟版本号 版本号一般取前几位就可以
			- 可以跟HEAD ~~~HEAD 表示当前版本 ^表示上一个版本 ^^表示上两个版本 HEAD~100表示前一百个版本
	# 查看命令记录
		+ git reflog
	# 撤销修改
                + git checkout -- <file> 
			`` 一种 readme.md修改后没有放到暂存区（git add ）,现在撤销就回到和版本库一模一样的状态。
			`` 一种 readme.md修改后已经放到暂存区，又做了修改，现在，撤销修改就回到添加到暂存区后的状态。
			`` -- 很重要，如果没有--就变成切换到另一个分支
	# 撤销暂存区修改
		+ git reset HEAD <file>
	# 删除文件 
		+ 删除已提交文件 
			- git rm <file>
		+ 本地文件删除了，但是服务器上没有删除
			- git checkout -- <file>
	# 将本地文件添加到远程仓库
		+ git remote add origin git@github.com:liule0206/Git-learn.git
			- liule0206 换成自己的用户名
			- 远程库的名字 Git-learn
	# 把本地文库内容全部推送到远程库上
		+ git push  -u Git-learn master
	# 
