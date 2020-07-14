##### SSMS

数据库管理工具L：以一种图形化的界面让用户方便快捷的操作数据库

1. 收集用户的请求，生成相应的命令，发送给服务器(本机Sql服务器的名称：`SQL Server(MSSQLSERVER)`)

2. 接受从服务器返回的数据，以图形化的界面显示

###### 列属性设置

- 默认值或绑定：未对字段赋值时则显示默认值
- 标识规范：用来设置起始值和增量（**int型才能设置标识列，一般标识列就是主键**）

##### 数据类型

**Image**：用来存储图像（二进制数据类型）

**char类型**：不指定长度时，默认是1

> charTest表，每个字段可存放10个字符（默认一字符一字节），即十字节

| Char(10) | Varchar(10) | Nchar(10) | Nvarchar(10) |
| -------- | ----------- | --------- | ------------ |
| aa       | aa          | aa        | aa           |

```sql
注释：--
--Len(参数)--计算指定参数的字符串个数，不区分大小写
--DataLength(参数)--计算指定参数的所占字节长度，一英文一字节，一中文二字节
select Len("aaa")	--3

--char--
--当存储的字符数量小于指定的空间的时候，空间不会收缩，大于的时候报错（截断二进制数据）
select DataLength(char) from charTest --10

--varchar--[需要做遍历回收多余空间]
--分配的空间是可变的动态空间，存储的字符长度小于分配空间是多于空间自动收缩，大于报错
select DataLength(varchar) from charTest --2

--nchar n--指unicode，即不管哪种字符都会使用2个字节存储。 [有中文时候使用nchar]
select DataLength(nchar) from charTest --20,十个字符，每字符2字节表示，所有20字节

--nvarchar
select DataLength(nvarchar) from charTest --4
```

##### 注意点

```sql
--1.没有"",所有的字符串都用''包裹
--2.没有"=="，赋值和逻辑相等都使用"=""
```

##### 创建数据库和表

```sql
--切换当前数据库
use master
--先判断数据库是否存在，如果存在就先删除
if exist(select * from sysdatabases where name='数据库名')
drop database 数据库名
-----------------------------

execute sp_configure 'show advanced options',1	--开启高级设置
RECONFIGURE
execute sp_configure 'xp_cmdshell',1
RECONFIGURE
go
--自动创建文件夹,调用存储过程xp_cmdshell，帮助我们创建一个文件夹d:\a\b\c
execute xp_cmdshell'mkdir d:\a\b\c'
```

##### 创建数据库

```sql
create database 数据库名
on [primary]	--在哪个文件祖上创建，默认在主文件组（primary,可省略）扩展名.mdf
(
--关于逗号：当其不是一句可以独立执行的sql命令时且是某结构的一句，添加,
name="逻辑名称_data",	--逻辑名称一般会有后缀，数据文件--data，日志文件--log 
size=初始大小,		--数值不应该包在''内
fileGrowth=增长方式,
maxsize=最大容量,
filename='全路径（绝对路径）'		--最后一句不添加,
),
filegroup 文件组名
(
name="逻辑名称_data1",	--次数据库文件，扩展名.ndf
size=初始大小,		
fileGrowth=增长方式,
maxsize=最大容量,
filename='全路径'		  
)
log on	--日志文件
(
name="逻辑名称_log",	--扩展名.ldf
size=初始大小,		
fileGrowth=增长方式,
[maxsize=最大容量,]		--一般不设置日志文件的最大容量
filename='全路径'		  
)
```

##### 创建表

```sql
create table 表名
(
	字段名称 字段类型 字段特征（是否为空 标识列 默认值 主键 唯一键 check约束）
)
--创建老师表Teacher Id、Name、Gender、Age、Salary、Brithday
create table Teacher
(
	Id int identity(1,1) primary key,	--设置标识列identity(标识种子，标识增量)
    Name nvarchar(20) not null,	--字段不能为空
    Gender bit not null,	--bit型数据，视图界面（设计）下只能输入 true和false
    Age int check(age>0 and age<=100) not null,
    Salary money null,	--字段为空时可以写也可以不写
    Birthday datetime not null default('2000-2-2')	--给了一个默认值
)
```

##### 完整性约束

**实体完整性**：表的每一行数据就称为一个实体，实体完整性即每一行记录是唯一的，不重复的

- 标识列：系统自动生成，永远不会空
- 主键唯一
- 唯一键：唯一但是可以为null，只能空一次 [右键-索引-添加-修改名称，修改类型，确定字段]