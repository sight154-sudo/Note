# SQL优化思路

## 基本命令

### 索引操作

~~~sql
## 查询索引
show index from tb;
## 添加索引
alter table name add [unique|fulltext|] index 索引名(列名[(索引长度)]);
create index idx_name on tb(`column`);

# 删除索引 
drop index 索引名 on 表名;
alter table 表名 drop index 索引名;
~~~





## 备份表

~~~sql
## 方式一
create table tb_back like src_db;
insert into tb_back select * from src_db;

## 方式二
create table tb_back as select * from src;

##　或者
create table tb_back(select * from src);
~~~



# 常用命令

## 表操作

~~~sql
-- 查询表详细信息
show create table t_name;
desc t_name;
show columns from t_user; -- 查询表列信息
show full columns from t_name; -- 查询表列所有信息
~~~



~~~sql
-- 字符集操作
alter database db_name default character set utf8 [collate utf8_bin]; -- 修改数据库字符集
alter table t_user convert to character set utf8 collate utf8_bin; -- 修改表所有字段字符集
alter table t_name character set utf8 [collate utf8_bin]; -- 修改表的字符集
alter table t_name default character set utf8 [collate utf8_bin]; -- 只修改表的默认字符集
alter table t_name change c_name c_name varchar(32) character set utf8 [collate utf8_bin]; -- 修改字段字符集
~~~



