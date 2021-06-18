#git 是分布式版本控制系统 svn 是集中式版本控制系统
集中式版本控制系统 需要联网才能更新,提交 容易出现单点故障导致代码丢失,
git 是每次克隆相当于一次备份，有仓库的全部代码，可以在不联网的情况也能自己在自己的工作空间工作
#git文件状态 已跟踪 和 未跟踪
已跟踪指已经被纳入版本控制系统中
未跟踪指未纳入版本控制系统中

#克隆远程仓库到本地(相当于svn的check out,区别在与clone是整个仓库的所有文件都会有一个备份) 
git clone https://github.com/liushengbao/study.git
#将本地目录转为git仓库
cd dir
git init
该命令将创建一个名为 .git 的子目录
git add .
git add 命令来指定所需的文件来进行追踪
git commit -m "comment"

#设置全局账户和邮箱
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com


#查看远程仓库的地址和仓库名称
git remote -v
#添加所有修改到缓冲区
git add .
#提交修改的内容
git commit -m 'log'
#推送修改到远程仓库 ...紧接着输入用户名和密码
git push origin master
#拉取远程仓库的变化(类似svn的update)
git pull https://github.com/liushengbao/book.git
#查看文件状态
git status
#跟踪一个文件，多次修改一个文件需要重新git add
git add fileName
#将暂存区内容添加到本地仓库中
git commit -m "注释"


#git 终端中文显示乱码解决
git config --global core.quotepath false


