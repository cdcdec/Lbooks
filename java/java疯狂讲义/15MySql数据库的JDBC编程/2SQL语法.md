# 2SQL语法
SQL语句是对所有关系数据库都通用的命令语句.
## 安装数据库


## 关系数据库基本概念和MySql基本命令
DBMS(DataBase Management System),数据库管理系统.
几种类型的数据库管理系统:
* 网状型数据库
* 层次型数据库
* 关系数据库
* 面向对象数据库

关系型数据库系统:
最基本的数据存储单元是数据表.可以将数据表想像成由行和列组成的表格,其中每一行被称为一条记录,每一列称为一个字段.

MySql数据库的一个实例(Server Instance)可以同时包含多个数据库.

* 查看当前实例下有多少个数据库:show databases;
* 删除指定的数据库:drop database 数据库名;
* 创建新的数据库:create table [if not exists] 数据库名;
* 进入某数据库:use 数据库名;
* 查询某数据库下包含多少个数据表:show tables;
* 查看指定数据表的表结构(查看该表有多少列,没列的数据类型等信息):desc 表名;
* 启动MySql命令行客户端:mysql -p 密码 -u 用户名 -h 主机名


MySql支持的两种存储机制:
* MyISAM:早期默认的存储机制,对事务支持不够好;
* InnoDB:InnoDB提供事务安全的存储机制;
MySql5.0以上的数据库系统,系统默认使用InnoDB存储机制,如果不想使用InnoDB表,则可以使用skip-innodb选项.如果需要在建表时显示指定存储机制,则可在标准建表语法的后面添加下面任意一句:
* ENGINE=MyISAM---->强制使用MyISAM存储机制;
* ENGINE=InnoDB---->强制使用InnoDB存储机制;

## SQL语句基础
SQL的全称是Structured Query Language,也就是结构化查询语言,是操作和检索关系数据库的标准语言.使用SQL语句,程序员和数据库管理员(DBA)可以完成如下任务:
* 在数据库中检索信息;
* 对数据库的信息进行更新;
* 该表数据库的结构;
* 更改系统的安全设置;(通常由DBA完成)
* 增加用户对数据库或表的许可权限(通常由DBA完成).
标准的SQL语句通常分为如下几种类型:
* 查询语句:主要由select关键字完成,语句最复杂,功能最丰富;
* DML(Data Manipulation Language,数据操作语言)语句:主要由insert,update和delete完成;
* DDL(Data Definition Language,数据定义语言)语句:create,alter,drop,truncate;
* DCL(Data Control Language,数据控制语言)语句:grant,revoke;
* 事务控制语句:主要由commit,rollback和savepoint三个关键字完成;
>SQL语句中的关键字不区分大小写;
>SQL语句的标识符:必须以字母开头,可以包含字母,数字,警号,下划线,美元符;不能使用当前数据库系统的关键字,保留字,建议多个单词连缀而成,单词之间以下划线分割;

### DDL语句
DDL语句是操作数据库对象的语句,包括创建(create),删除(drop)和修改(alert)数据库对象.
常见的数据库对象:
* 表(对应关键字:table):表是存储数据的逻辑单元,以行和列的形式存在,列是字段,行是记录;
* 数据字典:系统表,存放数据库相关信息的表,由数据库系统维护,程序员只可查看系统表的数据;
* 约束(关键字:constraint):执行数据校验的规则,用于保证数据完整性的规则;
* 视图(view):一个或多个数据表里数据的逻辑显示,视图并不存储数据;
* 索引(index):用于提高查询性能,相当于数的目录;
* 函数(function):用于完成一次特定的运算,具有一个返回值;
* 存储构成(procedure):用于完成一次完整的业务处理,没有返回值,但可通过传出参数将多个值传给调用环境;
* 触发器(trigger):相当于一个事件监听器,当数据库发生特定事件后,触发器被触发,完成相应的处理;

>操作数据库对象:create table,create view,create index...

#### 创建表的语法
```txt
//每个列定义之间用英文逗号隔开,最后一个列定义不使用英文逗号.
create table [模式名] 表名{
    #列定义
    列名1  类型  [默认值],
    列名2  类型  
}


```
MySql支持的列类型:
* tinytext/text/mediumtext/longtext  1字节/2字节/3字节/4字节的文本对象,可用于存储超长长度的字符串,分别可存储255B/64KB/64MB/4GB大小的文本
* 
。。。。。

#### 修改表结构的语法
修改表结构使用alter table,修改表结构包括增加列定义,修改列定义,删除列,重命名列等操作.
增加列定义的语法:
```txt
alter table 表名 add{
    #可以有多个列定义
    列名1  类型  [默认值],
    列名2  类型
}
```
修改列定义的语法如下:
```txt
alter table 表名 modify{
    #MySql的一个modify命令不支持一次修改多个列定义,Oracle支持;
    列名1  类型  [默认值];
}
```
删除列:
```txt
alter table 表名 drop 列名;

```
重命名数据表(MySQL特有语法):
```txt
alter table 表名 rename to 新表名;
```
改变列名(MySQL特有语法):
```txt
alter table 表名 change 原表名 新表名  类型 [default expr] [first|after col_name]
```
#### 删除表的语法
drop table 表名;

#### truncate表
一次性删除整个表的全部记录,但保留表结构.语法:truncate 表名;
比delete速度快;


### 数据库约束
约束是在表上强制执行的数据校验规则,约束主要用于保证数据库里数据的完整性,除此之外,当表中数据存在相互依赖性时,可以保护相关的数据不被删除.大部分数据库支持下面5种完整性约束:
* not null:非空约束,指定某列不能为空;
* unique:唯一约束,指定某列或者几列组合不能重复;
* primary key:主键,指定该列的值可以唯一标识该条记录;
* foreign key:外键,指定改行记录从属于主表中的一条记录,主要用于保证参照完整性;
* check:检查,指定一个布尔表达式,用于指定对应列的值必须满足该表达式;(MySQL不支持check约束)

为数据库指定约束的时机:
* 在建表的同时为相应的数据列指定约束;
* 建表后创建,以修改表的方式来增加约束;

>MySQL使用information_schema数据库里的TABLE_CONSTRAINTS表来保存该数据库实例中所有的约束信息。

####　not null约束
确保指定列不能为空,只能作为列级约束使用.SQL中的not null,不区分大小写.且所有数据类型的值都可以是null;
* 建表时指定列非空约束:在列定义后增加not null;
* 修改表时增加或删除非空约束:
```txt
//增加非空约束
alter table 表名 modify 列名 类型  not null;
//取消非空约束
alter table 表名 modify 列名  类型 null;
//取消非空约束,并指定默认值
alter table 表名 modify 列名 类型 default 默认值 null;

```
#### unique约束


create table if not exists catalog(id int primary key AUTO_INCREMENT NOT NULL,urlPath varchar(150)  not null unique,title varchar(60)  not null unique,volume varchar(10)  not null unique,mainTitle varchar(30) not null unique,secondTitle varchar(10) not null,type varchar(6) not null);

CREATE TABLE IF NOT EXISTS chapter(id int primary key AUTO_INCREMENT NOT NULL,title varchar(150) not null unique,explainText mediumtext,translationText mediumtext,originalText  mediumtext,volumeNum int not null unique);




