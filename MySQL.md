# DDL

#### 数据库操作

```sql
show database

create database 数据库名

create database if not exists 数据库名 default charset 字符编码 collate 排序

drop database 数据库名
```

#### 表操作

```sql
create table 表名(
	列名 数据类型 [列级约束],
    ...
    [,表级约束]
)

alter table 表名
[add 新列名 数据类型 [列级约束]]
[drop column 列名 [restrict| cascade]]
[alter| modify column 列名 数据类型 [列级约束]]

drop table 表名
```

##### SQL数据类型

> 字符串
>
> - char(n)
> - varchar(n)
>
> 数字
> - smallint
> - int
> - bigint
> - float
> - double
>
> 日期
>
> - data
> - time
> - year
> - datatime

##### 约束

> 列级约束条件
>
> - 主键 primary key
> - 外键 foreign key
> - 唯一 unique
> - 检查 check(MySQL不支持)
> - 默认 default
> - 非空/空值 not null/ null
>
> 表级约束条件
>
> - 主键,外键,唯一,检查
>
> ```sql
> [constraint <外键名>] 
> foreign key 字段名 [,字段名,...] 
> references <主表名> 主键列[,主键列,...]
> ```

# DML

#### 插入

```sql
insert into 表名 
values(值1, 值2, ...)

insert into 表名(列名1, 列名2, ...) 
values(值1, 值2, ...) [,(值1, 值2, ...)]
```

#### 修改

```sql
update 表名 
set 列名1 = 值1 , 列名1 = 值2, ...
where 条件
```

#### 删除

```sql
delete from 表名 
where 条件
```

# DQL

#### 查询

```sql
select [distinct] 列名1 别名1, 列名2 别名2, ...
from 表名1 别名1, 表名2 别名2, ...
where 条件 
order by 列名 [asc| desc]

```

#### 分组和分页查询

```sql
select sum(*) 
from 表名 
where 条件 
group by 列名 
having 条件

select *
from 表名
limit 起始位置,数量
```

#### 外连接查询

```sql
select * 
from 表名
[inner| left| right] join 表名
on 条件
```

#### 嵌套查询

```sql
select * 
from 表名
where 列名 = (
	select 列名 
    from 表名
    where 条件
	)
```



##### 条件

> 比较
>
> - =, >, <, >=, <=, != 等
>
> 集合
>
> - in, not in
>
> 模糊
>
> - like, not like
>
> 连接
>
> - and, or, not



##### 聚集函数

> - count([distinct] *)
> - count([distinct] 列名)
> - sum([distinct] 列名)
> - avg([distinct] 列名)
> - max([distinct] 列名)
> - min([distinct] 列名)

# DCL

#### 创建用户

```sql
create user 用户名 [identified by 密码]
```

#### 登录用户

```cmd
login -u用户名 -p密码
```

用户授权

```sql
grant all| 权限1, 权限2, ... (列1, ...) on 数据库.表 to 用户 [with grant option]

revoke all| 权限1,权限2, ... (列1,...) on 数据库.表 from 用户
```

# 视图

```sql
create view 视图名称(列名) as 子查询语句 [with check option]

drop view 视图名
```



# 索引

```sql
create index 索引名 on 表名(列名)

show index from 表名

drop index 索引名 on 表名
```



# 触发器

```sql
create trigger 触发器名 [before| after] [insert| update| delete]
on 表名/ 视图名 for each row
-- delete from 表名 where old.列名 = 表名.列名

show triggers

drop trigger 触发器名
```



# 事务

```sql
show engines

begin
...
rollback
savepoint 回滚点
rollback to 回滚点
...
commit
```

#### ACID

> 原子, 一致, 隔离, 持久

​                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
