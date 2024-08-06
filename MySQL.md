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
create [fulltext| spatial| unique] index 索引名 on 表名(列名) 

show index from 表名

drop index 索引名 on 表名

select * from 表名 where match(列名) against("关键字")
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

#### 锁机制

```sql
set session transaction isolation level 隔离级别

flush tables with read lock

lock table 表名 read/ write

语句... lock in share mode

语句... for update

unlock tables
```

##### 隔离级别

> - 读未提交: read uncommited
>
> - 读已提交: read commited
> - 可重复读:repeated read 
> - 串行读: serialization

##### 行锁类型

> - 记录锁 record locks
> - 间隙锁 gap locks
> - 临键锁 next-key locks

# 函数

#### 自定义函数

```sql
create function 函数名(参数 类型) return 类型
begin
	declare 变量名称 变量类型[, ...];
	declare 变量名称 变量类型 default 默认值;
	set 变量名 = 值;
	
	if 表达式 then
		表达式;
	else 
		表达式;
	end if;
	
	case [表达式]
		when 表达式 then 
			表达式;
		else
			表达式;
	end case;
	
	while 表达式 do
		表达式;
	end while;
	
	循环名: loop
		表达式;
		leave 循环名;
	end loop 循环名;
	
	repeat
		表达式;
	until 表达式 end repeat;
	
	return 表达式 ;
end


drop function if exists 函数名
```

#### 全局变量

```sql
set @变量名 = 值

show global variables
```

#### 字符串

> substring( 列名, 下标1, 下标2)
>
> left( 列名, 长度)
>
> right( 列名, 长度)
>
> concat( 字符串, 字符串)
>
> replace( 列名, 源字符串 , 目标字符串)
>
> upper( 字符串)
>
> lower( 字符串)
>
> length( 字符串)

#### 日期

> date_add( 日期, interval 增量 单位)
>
> datedifff( 日期1, 日期2)
>
> curdate()
>
> curtime()
>
> now()

#### 数学

> abs(x)
>
> ceiling(x)
>
> floor(x)
>
> round(x, 精度)
>
> exp(x)
>
> rand(x)
>
> log(x)
>
> pi()
>
> power(x, n)
>
> sqrt(x)
>
> sin(x) cos(x) tan(x)

#### 类型转换

> cast(数据 as 数据类型)
>
> binary[(n)]
>
> char[(n)]
>
> date
>
> datetime
>
> decimal[( m(, n)]
>
> signed[integer]
>
> time
>
> unsigned[interger]

#### 流程控制

> if(条件表达式, 结果1, 结果2)
>
> ifnull(值1, 值2)
>
> nullif(值1, 值2)
>
> isnull(值)
>
> sleep(值)

```sql
case 值
	when 条件 then
		结果
	when 条件 then
		结果
	...
	else
		结果
end

case 
	when 值 条件 then
		结果
	when 值 条件 then
		结果
	...
	else
		结果
end
```

# 存储过程

```sql
create procedure 过程名([in| out| inout] 参数 类型, ...)
begin
	declare 游标名 cursor for 查询结果;
	declare (continue/ exit) handler for 异常名 表达式;
	open 游标名;
	fetch 游标名 into 标量
	close 游标名;
	
	表达式;
end

call 过程名(参数, ...)
```

