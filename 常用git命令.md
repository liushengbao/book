#克隆远程仓库到本地
git clone https://github.com/liushengbao/book.git
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


