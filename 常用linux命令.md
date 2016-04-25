##linux查询某个端口本什么进程占用
lsof -i
##linux查询进程们都占用了哪些端口
netstat -nlapt
##linux测试某台机器某个端口是否可以被连接
telnet ip port 
##linux查看文件的md5值用于判断两个文件是否一样
md5sum filename
