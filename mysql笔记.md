��������ĳtext �ֶΰ���ĳЩ�ַ�������
SELECT role_name,arg02_json FROM cross_role WHERE find_in_set('"worldZoneId":1}', arg02_json); 
�����û�
CREATE USER lsb IDENTIFIED BY 'password';
grant ����Ȩ��
GRANT ALL PRIVILEGES ON db1.* TO 'lsb'@'localhost' IDENTIFIED BY 'password';
������ip localhost �� lsb ���� db1 ������б������Ȩ��,���趨���ӿ��� password
ȡ��Ȩ��
EVOKE ALL PRIVILEGES ON *.* FROM 'username'@'localhost'; 
ֻ��SELECT, UPDATEȨ��
GRANT SELECT, UPDATE ON wordpress.* TO 'username'@'localhost' IDENTIFIED BY 'password';
ˢ��Ȩ��
FLUSH PRIVILEGES;
ɾ���ղŴ������û�
DROP USER username@localhost;
//��ʾһ�����ܵ����б�
show full tables 
show tables 

��ʾĳ������ֶ�
show full fields from table_name;
describe table_name;

��ʾmysql �汾��
select version();
�鿴 ���еĴ�����
select * from information_schema.'TRIGGERS';

������(trigger)������ĳ�������������ĳ�ֲ�����
�����������﷨��Ҫ�أ�1.���ӵص�(table) 2.�����¼�(insert/update/delete) 3.����ʱ��(after/before) 4.�����¼�(insert/update/delete)
delimiter $
create trigger triggerName
after/before insert/update/delete on ����
for each row   #��仰��mysql�ǹ̶���
begin
sql���;
end;

truncate table `kf_merge_temp`  ���ĳ���������

�������
1.PRIMARY  KEY������������
mysql>ALTER  TABLE  `table_name`  ADD  PRIMARY  KEY (  `column`  ) 
2.UNIQUE(Ψһ����)
        mysql>ALTER  TABLE  `table_name`  ADD  UNIQUE (`column` ) 
3.INDEX(��ͨ����)
mysql>ALTER  TABLE  `table_name`  ADD  INDEX index_name (  `column`  )
4.FULLTEXT(ȫ������)
mysql>ALTER  TABLE  `table_name`  ADD  FULLTEXT ( `column` )
5.��������
mysql>ALTER  TABLE  `table_name`  ADD  INDEX index_name (  `column1`,  `column2`,  `column3`  )

UNIX ʱ�亯��
UNIXʱ���ת��Ϊ�����ú�����FROM_UNIXTIME()

����ת��ΪUNIXʱ����ú����� UNIX_TIMESTAMP()

locate�ǲ��ҵ�һ�������ڵڶ��������е�λ��, ������ʱ����ֵΪ0

concat�����Ӹ�������

delete�����dml,���������ŵ�rollback segement��,�����ύ֮�����Ч;�������Ӧ��trigger,ִ�е�ʱ�򽫱�����.  
truncate,drop��ddl, ����������Ч,ԭ���ݲ��ŵ�rollback segment��,���ܻع�. ����������trigger. 

����ĳ����ҵĵ����ֶ� 
update kf_dataext_player set bowsData = null where playerId = 230008662001;

���������� ĳ���ֶ���ֵ����
select playerId,bowsData from kf_dataext_player where bowsData is not null;
����
select playerId,bowsData from kf_dataext_player where char_length(bowsData) > 0;


 ������
 SELECT * FROM java LEFT JOIN mysql ON java.name=mysql.name;
 �Ҳ�����
 SELECT * FROM java RIGHT JOIN mysql ON java.name=mysql.name;


������ֶε�����    (schema ��Ҫ)  
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

��ĳ��������� ��information_schema  �� �ṩ�˵�ǰmysqlʵ�����������ݿ����Ϣ����
select engine from information_schema.TABLES where TABLE_NAME = 'kf_player' and TABLE_SCHEMA = 'kungfu_qq';


select playerName,info.gunScore from dt_player player inner join  dt_player_data_info info on player.playerId = info.playerId where info.gunScore>0;

set profiling =1;

//���õ�ǰ�غϵ�������뼶��
SET session transaction isolation level read committed;

