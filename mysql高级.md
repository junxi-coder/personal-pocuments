## 索引

创建索引：CREATE INDEX 索引名 ON 表名(字段名));
查看索引：SHOW INDEX FROM <表名> 
删除索引：DROP INDEX <索引名> ON <表名>

##### 1.查看sql查询次数

show [global,session] status like 'Com_______' 七个下划线  

##### 2.查看慢查询日志是否开启

show variables like 'slow_query_log'
#开启慢查询日志 修改mysql配置文件/etc/my.cnf
#开启慢查询日志开关
slow_query_log =1
#设置慢查询日志时间 超过则会视为慢查询记录下日志
long_query_time =2
#慢查询日志文件位置
/var/lib/mysql/localhost-slow.log
#重启mysql
systemctl restart mysqld
#实时记录数据更新命令
tail -f 文件名

##### 3.通过profile详情定位sql耗时位置

#查看profile是否支持
select @@hava_profiling
#查看profile是否开启
select @@profiling
#开启profile
SET (global,session)profiling =1
#查看sql耗时情况
show profiles；
#查看某条sql具体耗时问题
show profile <cpu>for query query_id

##### 4.explain执行计划

EXPLAIN/desc select语句
#explain参数意义
id id相同由上到下执行  id不同 id值越大执行优先级越高
type 表示连接类型
性能由好到坏 null system const eq_ref ref range index all
key 表示用到的索引
key_len 表示索引长度
filtered 表示展示的结果行数占查询总行数的百分比
extra  需要回表/不需要回表

##### 5.索引的使用

#最左前缀法则
#不要在索引字段上运算
#字符串类型索引字段要加引号
#索引字段不能首字符模糊查询
#or 两侧必须都有索引
#mysql数据评估
#覆盖索引
#前缀索引 处理大文本字段 降低索引体积
#索引选择
select 字段 from 表名 use index(索引名字)

------

### sql优化



#### insert优化

- 批量插入 
- 手动提交事务 start  transaction    commit
- 主键顺序插入
- 大批量插入 load指令



#### 主键优化

- 页合并
- 页分裂

![image-20220926175837862](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220926175837862.png)

- 主键设计原则

  ![image-20220926180115777](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220926180115777.png)





#### order by优化

![image-20220926180429706](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220926180429706.png)

![image-20220926181035239](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220926181035239.png)

![image-20220926181055089](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220926181055089.png)

###### ！！！要用到覆盖索引

排序还可以通过增大缓冲区降低排序时间

![image-20220926181401448](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220926181401448.png)





#### group by优化

![image-20220926181920404](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220926181920404.png)





#### limit优化

![image-20220926182353184](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220926182353184.png)

#### count优化

放到缓存中 自己进行计数

![image-20220926182955221](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220926182955221.png)



#### update优化

![image-20220929163247406](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220929163247406.png)



# 锁

#### 全局锁  

使用场景：**数据库备份**

![image-20220929164723718](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220929164723718.png)

![image-20220929165831432](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220929165831432.png)

mysqldump -h ip -uroot -p123456 dateBaseName > table.sql

------

#### 表级锁

![image-20220929170304493](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220929170304493.png)

