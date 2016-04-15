搜索表中某text 字段包含某些字符串的行
SELECT role_name,arg02_json FROM cross_role WHERE find_in_set('"worldZoneId":1}', arg02_json); 
创建用户
CREATE USER lsb IDENTIFIED BY 'password';
grant 分配权限
GRANT ALL PRIVILEGES ON db1.* TO 'lsb'@'localhost' IDENTIFIED BY 'password';
给来自ip localhost 的 lsb 赋予 db1 库的所有表的所有权限,并设定连接口令 password
取消权限
EVOKE ALL PRIVILEGES ON *.* FROM 'username'@'localhost'; 
只给SELECT, UPDATE权限
GRANT SELECT, UPDATE ON wordpress.* TO 'username'@'localhost' IDENTIFIED BY 'password';
刷新权限
FLUSH PRIVILEGES;
删除刚才创建的用户
DROP USER username@localhost;
//显示一个库总的所有表
show full tables 
show tables 

显示某个表的字段
show full fields from table_name;
describe table_name;

显示mysql 版本号
select version();
查看 所有的触发器
select * from information_schema.'TRIGGERS';

触发器(trigger)：监视某种情况，并触发某种操作。
触发器创建语法四要素：1.监视地点(table) 2.监视事件(insert/update/delete) 3.触发时间(after/before) 4.触发事件(insert/update/delete)
delimiter $
create trigger triggerName
after/before insert/update/delete on 表名
for each row   #这句话在mysql是固定的
begin
sql语句;
end;

truncate table `kf_merge_temp`  清除某个表的数据

添加索引
1.PRIMARY  KEY（主键索引）
mysql>ALTER  TABLE  `table_name`  ADD  PRIMARY  KEY (  `column`  ) 
2.UNIQUE(唯一索引)
        mysql>ALTER  TABLE  `table_name`  ADD  UNIQUE (`column` ) 
3.INDEX(普通索引)
mysql>ALTER  TABLE  `table_name`  ADD  INDEX index_name (  `column`  )
4.FULLTEXT(全文索引)
mysql>ALTER  TABLE  `table_name`  ADD  FULLTEXT ( `column` )
5.多列索引
mysql>ALTER  TABLE  `table_name`  ADD  INDEX index_name (  `column1`,  `column2`,  `column3`  )

UNIX 时间函数
UNIX时间戳转换为日期用函数：FROM_UNIXTIME()

日期转换为UNIX时间戳用函数： UNIX_TIMESTAMP()

locate是查找第一个参数在第二个参数中的位置, 不存在时返回值为0

concat是连接各个参数

delete语句是dml,这个操作会放到rollback segement中,事务提交之后才生效;如果有相应的trigger,执行的时候将被触发.  
truncate,drop是ddl, 操作立即生效,原数据不放到rollback segment中,不能回滚. 操作不触发trigger. 

更新某个玩家的单个字段 
update kf_dataext_player set bowsData = null where playerId = 230008662001;

搜索整个表 某个字段有值的行
select playerId,bowsData from kf_dataext_player where bowsData is not null;
或者
select playerId,bowsData from kf_dataext_player where char_length(bowsData) > 0;


 左部连接
 SELECT * FROM java LEFT JOIN mysql ON java.name=mysql.name;
 右部连接
 SELECT * FROM java RIGHT JOIN mysql ON java.name=mysql.name;


计算该字段的数量    (schema 概要)  
SELECT count(*) 
FROM information_schema.COLUMNS 
WHERE TABLE_SCHEMA = 'gongfu_s1' 
AND TABLE_NAME = 'kf_dataext_player' 
AND COLUMN_NAME = 'bowsData'


select * from (
SELECT count(*) count_num, sch.TABLE_SCHEMA schema_name
FROM information_schema.COLUMNS sch
WHERE  TABLE_NAME = 'kf_dataext_player' AND COLUMN_NAME = 'armorData'
group by sch.TABLE_SCHEMA order by sch.TABLE_SCHEMA asc
) aa
where aa.count_num=0
;

查某个表的引擎 （information_schema  ： 提供了当前mysql实例中所有数据库的信息。）
select engine from information_schema.TABLES where TABLE_NAME = 'kf_player' and TABLE_SCHEMA = 'kungfu_qq';


select playerName,info.gunScore from dt_player player inner join  dt_player_data_info info on player.playerId = info.playerId where info.gunScore>0;

set profiling =1;

//设置当前回合的事务隔离级别
SET session transaction isolation level read committed;

