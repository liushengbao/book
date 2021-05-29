#克隆远程仓库到本地(相当于svn的check out,区别在与clone是整个仓库的所有文件都会有一个备份) 
git clone https://github.com/liushengbao/study.git
#将本地目录转为git仓库
cd dir
git init
该命令将创建一个名为 .git 的子目录
git add .
git add 命令来指定所需的文件来进行追踪
git commit -m "comment"


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


