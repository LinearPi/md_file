###mysql使用

链接数据库：

mysql -uroot -p密码

####创建

mysql 语法，每次命令之后接分号，    

创建database：

create database 数据库名；

使用database：

use 数据库名；

MySQL支持多种类型，大致可以分为四类：**数值型、浮点型、日期/时间和字符串(字符)类型**。 

| 命令           | 创建的类型 | 大小(字节)   |
| -------------- | ---------- | ------------ |
| int            | 整型       | 1            |
| float          | 浮点型     | 4            |
| double         | 双精度     | 4            |
| char           | 字符型     | 0~255        |
| text           | 文本       | 0~65535      |
| set            | 集合       | 1~8          |
|                |            |              |
| primary key    | 主键       | 见下面的例子 |
| FOREIGN KEY    | 外键       |              |
| NOT NULL       | 不能为空   |              |
| auto_increment | 自增长     |              |

例子:

```mysql
CREATE TABLE `dage` (
 `id` int(11) NOT NULL auto_increment,
 `name` varchar(32) default '',
 PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8；

CREATE TABLE `xiaodi` (
 `id` int(11) NOT NULL auto_increment,
 `dage_id` int(11) default NULL,
 `name` varchar(32) default '',
 PRIMARY KEY (`id`),
 KEY `dage_id` (`dage_id`),
 CONSTRAINT `xiaodi_ibfk_1` FOREIGN KEY (`dage_id`) REFERENCES `dage` (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8；
```



时间和日期类型

| 时间 | 用途 | 格式 | 大小(字节) |
| ---- | ---- | ---- | ---- |
| date        | 时间                    | YYYY-MM-DD | 3 |
| time        | 时间值或持续时间        | HH:MM:SS | 3 |
| year        | 年份值                  | YYYY | 1 |
| datetime    | 混合日期和时间值        | YYYY-MM-DD<br />HH:MM:SS | 8 |
| timetamp    | 混合日期,时间值或时间戳 | YYYYMMDD<br />HHMMSS | 8 |




#### python链接mysql数据库

```python
# python3 链接mysql

import pymysql.cursors

conn(
	host='118.24.26.162',  # ip地址，如果是本地填localhost
    port=3306,  # 端口号
    user='root',  # 使用的用户名
    password='li123456',  # 密码
    db='lotterydb', # 数据库的名字
    charset='utf8'  # 编码方式
)  # 链接数据库

   # 获取游标
    cursor = conn.cursor()
    # 创建表单
    sql_table = "CREATE TABLE qxc (date int(5), data int(7)zerofill)"  # mysql 语句
    cursor.execute(sql_table)   # 执行mysql语句
    conn.commit()  # 确认mysql语句，并执行。
    cursor.close()  # 游标关闭
    conn.close()   #数据库链接关闭
```

#### 增删改查

​									表结构


| 操作类型   | 命令                                                         |
| :--------- | :----------------------------------------------------------- |
| 创建数据库 | CREATE DATABSE 数据库名；                                    |
| 创建表     | CREATE TABLE  表名（字段一 字段类型，字段二 字段类型）       |
| 使用数据库 | USE 数据库名;                                                |
| 插入数据   | INSERT INTO qxc (字段一, 字段二) VALUES ( '%s', '%s' )  %÷（value1，value2）; |
| 使用format | INSERT INTO qxc (字段一, 字段二) VALUES (f '{},{}'.format(value1，value2); |
| 删除数据库 | DROP 数据库名  ;                                             |
| 删除表     | DROP 表名;                                                   |
| 查询数据   | SELECT  * FROM 表名 on 条件一  where 条件二;                 |
| 删         | delete from 表名 where 限制条件；                            |
| 改         | UPDATE 表名 SET 字段名1=值1，[ ，字段名2=值2，…]   where [条件] |
| 增         | insert into 表名(字段1,字段2,……) values(值1,值2，……);        |
| join       | ==inner join 不会自动填充;                                   |
| left join  | 向右加入数据，如果没有的用0表示;                             |
| 排序       | order by                                                     |
| 组合       | group by                                                     |
| 限制       | limit                                                        |
|            | having和where区别                                            |


​										查询

Table: diet

| species(string) | food(string) |
| --------------- | ------------ |
| llama           | plants       |
| brown bear      | fish         |
| brown bear      | meat         |
| brown bear      | plants       |
| orangutan       | plants       |
| orangutan       | insects      |

```mysql
上面的例子的查询语句 
select column form diet where limiting;
select food form diet where species='orangutan';
```

Table: animals

| name(string) | species(string) | brithdate(date) |
| ------------ | --------------- | --------------- |
| Max          | gorilla         | 2001-01-13      |
| Sue          | gorilla         | 1998-06-12      |
| Max          | moose           | 2012-02-20      |
| Alison       | llama           | 1997-11-25      |
| George       | gorilla         | 2011-12-10      |
| Spot         | iguana          | 2010-07-23      |
| Ratu         | orangutan       | 1989-09-15      |
| Eli          | llama           | 2002-02-22      |

​								关联查询

```mysql
select animals.name animals.species diet.foot from animals join diet on animals.species=diet.species where food='fish'
```

```
这是内链接 和外连接 时的连接条件 
from 表1 join 表2 on 表1.字段=表2.字段 
on 相当于 from 表2，表2 where 表1.字段 = 表2.字段

animals, name,species  ---|
																  avg/max/min/sum
						join on species -->   restriction(约束)   -->  count
						name, species foot      foot='fish'      aggregation(聚合)
diet, species, foot   ---|^
```

| aggregation(聚合) 函数名称 | 作用                           |
| -------------------------- | :----------------------------- |
| COUNT()                    | 返回某列的行数                 |
| SUM()                      | 返回某列值的和                 |
| AVG()                      | 返回某列的平均值               |
| MAX()                      | 返回某列的最大值               |
| MIN()                      | 返回某列的最小值               |
| 例子                       | SELECT COUNT(*) FROM student2; |

增删改查：

```mysql
查
select  语句
where 子句表示限制条件--从表格中过滤出符合特定规定的行, where支持等于,不等于和布尔运算符
	where species ='gorilla' 仅返回物种列的值为'gorilla'的行,
	where name >= 'George' 仅返回名称列在"Georga"之后(按字母顺序)的行
    where species!='gorilla' and name != "Georga" 仅返回物种不是'gorilla'并且名称不是"Georga"的行

limit / offset
limit 子句对结构表格可以返回的行数做出限制.可选offset子句表示要在结果中跳过多少行.所以 limit 10 offset 100 讲返回10条结果, 从第101行开始.

order by
order by 子句告诉数据库如果进行排序,通常根据一个或多个列, 所有 order by species, name 表示首先安装物种列排序,然后在每个物种里按照名称排序.
排序发生在 limit/offset 之前,所有你可以使用它们来提取出按字母顺序排列的页面结果( )
可选desc 修饰符告诉数据库按照降序对结果排序 例如从大到小,从Z到A.

group by
group by子句只能用于汇总, 例如max或sum 没有group by子句的话, 对集合执行选择语句讲对整个选定表格进行汇总,只返回一行, 对于group by子句, 它将对group by 子句中的列或表达式的每个唯一值返回一行.

其他控制条件
1.in   2.between and   3.空值（Null）   4.DISTINCT  5.and 6.or  

自查 在一个表里面自己与自己组合查询
select 
	a.name, b.name 
from 
	animals as a, animals as b
where
	a.species = b.species and a.brithdate > b.brithdate

```

```mysql
增
insert into 表名(字段1,字段2,……) values(值1,值2，……);  
insert into 表名  values(值1,值2，……);      如果没有指定字段名，添加的值的顺序和字段在表中的顺序完全一致。
如果字段没有添加相应的数据，则会用Null来占位。
可以一次填写多条数据
insert into 表名  values
	(值1,值2，……)，
	(值3,值4，……)，
	(值5,值6，……);  
```

```mysql
删
delete from 表名 where 限制条件
删除全部数据 DELETE FROM 表名；
delete from 字段名；
删除全部有字段的名字
```

```mysql
改数据
UPDATE 表名
    SET 字段名1=值1，[ ，字段名2=值2，…]
    [ WHERE 条件表达式 ]；
例子：
UPDATE student 
    SET name=‘caocao’,grade=50
    WHERE id=1;
```

```mysql
当我们需要修改数据表名或者修改数据表字段时，就需要使用到MySQL ALTER命令。
mysql> create table testalter_tbl
    -> (
    -> i INT,
    -> c CHAR(1)
    -> );
    
ALTER 命令及 DROP 子句来删除以上创建表的 i 字段：
ALTER TABLE testalter_tbl  DROP i;
ADD 子句来向数据表中添加列，如下实例在表 testalter_tbl 中添加 i 字段，并定义数据类型
ALTER TABLE testalter_tbl ADD i INT;
如果需要修改字段类型及名称, 你可以在ALTER命令中使用 MODIFY 或 CHANGE 子句 。	

把字段 c 的类型从 CHAR(1) 改为 CHAR(10)，可以执行以下命令:
mysql> ALTER TABLE testalter_tbl MODIFY c CHAR(10);

使用 CHANGE 子句, 语法有很大的不同。 在 CHANGE 关键字之后，紧跟着的是你要修改的字段名，然后指定新字段名及类型。尝试如下实例：
mysql> ALTER TABLE testalter_tbl CHANGE i j BIGINT;
mysql> ALTER TABLE testalter_tbl CHANGE j j INT;
修改表名
ALTER TABLE testalter_tbl RENAME TO alter_tbl;
```



```mysql
对查询结果进行操作
    SELECT * FROM student2　ORDER BY grade; 排序
    SELECT * FROM student2　ORDER BY grade DESC; 降序
在对表中数据进行统计的时候，可以使用GROUP BY 按某个字段或者多个字段进行分组，
SELECT  字段名1，字段名2，… ROM 表名 ROUP BY 字段名1，字段名2，… [ HAVING 条件表达式 ];
    1.SELECT * FROM student2 GROUP BY gender;
    2.GROUP BY 和聚合函数一起使用
    2.SELECT COUNT(*) ,gender FROM student2 GROUP BY gender;
    3.GROUP BY 和 HAVING 关键字一起使用：HAVING 关键字可以跟聚合函数，而WHERE 关键字不能
    3.SELECT sum(grade),gender FROM student2 GROUP BY gender HAVING SUM(grade) < 300;
```

