#redis笔记

启动redis
redis-server /usr/local/etc/redis.conf
连接redis
redis-cli -h 127.0.0.1 -p 6379

#redis 数据结构
string 
字符串可以存储字符串，整数，浮点数
hash
list 
set 
sortedset

#redis 命令
#操作字符串
incr key-name 自增
decr key-name 自减
incrby key-name value 将key-name存储的值加上value
decrby key-name value 将key-name存储的值减去value
incrbyfloat key-name floatvalue 将key-name存储的值加小数
append key-name value 字符串追加值在末尾
getrange key-name start end 获取字符串范围的值 类似java substring
setrange key-name offset value 从start偏移位置的子串设置成value

#列表 偏移从0开始是
rpush key-name value1,value2 列表的右侧放入元素
lpush key-name value1,value2 列表的左侧放入元素
rpop key-name 移除列表最右端的元素并返回
lpop key-name 移除列表最左端的元素并返回
lindex key-name offset 返回列表偏移量为offset 的元素
lrange key-name start end 返回列表包含start end 的元素,,,lrange key-name 0 -1 为返回所有列表元素
ltrim key-name start end 对列表进行修剪,保留包含start end 范围内的所有元素

#集合
sadd key-name item...
srem key-name item...
sismember key-name item 检查元素是否在集合里面
scard key-name 集合的数量
srandmember key-name 从集合里面随机返回一个或多个元素
spop key-name 随机移除一个元素
smove source-key dest-key item 从source-key里移除成功后添加到dest-key集合




